+++
title = 'Google Summer of Code Week 5 and 6'
date = 2024-07-02T21:12:49+05:30
categories = ["GSoC", "PyBaMM", "NumFOCUS"]
type = ["post", "posts"]
tags = ["gsoc"]
series = ["gsoc"]
draft = false 
+++

{{< image src="https://user-images.githubusercontent.com/20817509/107091287-8ad46a80-67cf-11eb-86f5-7ebef7c72a1e.png" alt="PyBaMM" position="center" style="width:300px; border-radius: 8px;" >}}

# Fifth and sixth-week report
After I got the `entry points` for parameter sets working, it was time for `Model entry points`. If you haven't read about my previous blog post on parameter entry points, you can read it [here]({{< ref "GSoC Week 3-4.md" >}}).

## What are Model entry points?
Just like adding a third-party parameter set, you could even add your own models to a Python package to be accessed using PyBaMM. PyBaMM has a set of predefined models in its own library like the `BasicSPM`. Let us say just like a third-party parameter set, a user wants to add their own model without actually adding it to the PyBaMM. Now, for a researcher with limited knowledge in programming and development environments, it would be difficult for them to do so as PyBaMM doesn't support third-party models. They probably have to reverse engineer and understand the library codebase to get familiar with the model APIs to create a model instance and pass it on to PyBaMM for simulation.

## The approach to third-party models 
The idea for the model entry points is similar to that of parameter sets entry points, we have a `singleton instance` of 
`parameter_sets` and `models` sharing the same common API. Both of these instances get initialised when the `generated project` using cookiecutter is initialised and imported through Python after the installation as I have mentioned in my previous [blog]({{< ref "GSoC Week 3-4.md" >}}). The models can then be mapped through `pyproject.toml` and called using the `Model('Author/Model)` method. This method returns an `initialised object` of the model called.
```toml
[project.entry-points."models"]
SPM = "pybamm_cookiecutter.models.input.SPM:SPM"
```

## Testing the entry points and inside the generated project
Thanks to `github-actions` and `nox` I could automate most of the tests and separate out the sessions for `template-generation-tests` and `generated-project-tests`. The first one would test the proper generation of projects against multiple input prompts while the other would test if the units inside the generated projects are working well as intended.

## Demonstration 
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
## Now that the package is installed locally, you can access it in the Python shell
```
```Python
import pybamm_cookiecutter
list(pybamm_cookiecutter.models)
# Will return a list of parameter_sets in the entry point
['SPM', ...]
# Parameter set can be accessed using the parameter_sets entry point
model = pybamm_cookiecutter.Model('SPM')
print(model)
>>> <pybamm_cookiecutter.models.input.SPM.SPM object at 0x75d619a4fe00>
```

## Summary of my contributions
- Implemented `Model Entry Points` to create Model objects within the template and initialise them through entry points.
Added the SPM model which can be initialised through the model entry points.
A wrapper method to load a model object called models("modelname/authorname") is added.
Added two basic tests for model entry points - [PR #27](https://github.com/pybamm-team/pybamm-cookiecutter/pull/27)
- Added `doctests` in CI to test if the documentation builds using `sphinx` - [PR #25](https://github.com/pybamm-team/pybamm-cookiecutter/pull/25)

