+++
title = 'Google Summer of Code Week 3 and 4'
date = 2024-06-18T19:19:09+05:30
categories = ["GSoC", "PyBaMM", "NumFOCUS"]
type = ["post", "posts"]
tags = ["gsoc"]
series = ["gsoc"]
draft = false 
+++

{{< image src="https://user-images.githubusercontent.com/20817509/107091287-8ad46a80-67cf-11eb-86f5-7ebef7c72a1e.png" alt="PyBaMM" position="center" style="width:300px; border-radius: 8px;" >}}

# Third and fourth-week report
During the third week, after having a good grip on the project I moved on to working on the most important part of the project which were the **entry points**.

## What are entry points?
PyBaMM provides a variety of predefined `parameter sets` and `models` that can be used for different battery chemistries and configurations and simulations. These sets include parameters for various battery components and conditions, ensuring accurate simulations. In `PyBaMM`, a third-party parameter set can be manually added by creating a Python package and mapping it in `pyproject.toml` under the `[project.entry-points.pybamm_parameter_sets]` group. This would then load the parameter set through the `parameter_sets` instance within `PyBaMM` which could be then accessed by a user.

## Problems with third-party entry points
Due to the lack of extensive programming knowledge, especially in the area of the Python development ecosystem, researchers using `PyBaMM` find it difficult to set up a python package and add their entry points to the project. That's where my project comes in, what if there was a way you could set up a python package that accommodates the features of PyBaMM and you could initialise it with one command? Later you could add your third-party parameter sets and models in that package and test it! Without having to go through the overwhelming hassles of setting up a python package for your third-party parameter sets.

## The solution
The solution was a `cookiecutter template` with `entry points API`, that a user could use to add and map their own third-party `parameter_sets`. With this `API` you could access your own `parameter_sets` and pass them to `PyBaMM` directly without any type conversions.

### Demonstration
```bash
## First install cookiecutter using pip
pip install cookiecutter
## Generate a project using cookiecutter 
cookiecutter pybamm-cookiecutter/
## Install the generated project in editable mode using pip
cd pybamm-cookiecutter
nox -s dev 
## Or alternatively 
pip install -e .[dev]
## Now that the package is installed locally, you can access it in Python shell
```
```Python
import pybamm_cookiecutter
list(pybamm_cookiecutter.parameter_sets)
# Will return a list of parameter_sets in entry point
['Chen2020', ...]
# Parameter set can be accessed using the parameter_sets entry point
ps = pybamm_cookiecutter.parameter_sets["Chen2020"]
```

This is similar to how parameter sets instance works in PyBaMM and doesn't require adaptation or learning new methods to use this. You can refer the full documentation [here](https://docs.pybamm.org/en/latest/source/api/parameters/parameter_sets.html).

## Summary of my contributions
- Added `parameter_sets` instance, a parameter set (`Chen2020`) and a few `nox-sessions` for tests and editable installation of the `generated project` - [PR #15](https://github.com/pybamm-team/pybamm-cookiecutter/pull/15)

