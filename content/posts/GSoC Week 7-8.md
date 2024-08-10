+++
title = 'Google Summer of Code Week 7 and 8'
date = 2024-07-17T12:09:49+05:30
categories = ["GSoC", "PyBaMM", "NumFOCUS"]
type = ["post", "posts"]
tags = ["gsoc"]
series = ["gsoc"]
draft = false
+++

{{< image src="https://user-images.githubusercontent.com/20817509/107091287-8ad46a80-67cf-11eb-86f5-7ebef7c72a1e.png" alt="PyBaMM" position="center" style="width:300px; border-radius: 8px;" >}}

# Seventh and eighth-week report
Model entry points are now working and production-ready. Finally, the project was coming in one piece and they were ready to be tested with battery models.

## The entry points API and unifying them
As mentioned in my last blog, `parameter sets` and `models` needed to have entry points so users could add their own third-party models to use within PyBaMM. While the current working of parameter set entry points and model entry points were discrete, they could be unified as their behaviour was almost the same.

## How do entry points work?
An entry point works by loading the metadata from `pyproject.toml` and mapping it to a specific function mentioned in the entry point value. The metadata from a group is read and loaded, and in the case of a parameter set, the entry point is mapped to a `get_paramater_values()` method, which when loaded gets called automatically. As in the case of the models, the entry point is mapped to the parent battery model class which gets initialised, and returns an initialised battery model object when loaded.

## The unification of parameter sets and model entry points API
As mentioned, both these APIs had the same behaviour, while one was getting the entry points from the `parameter_sets` group under `pyproject.toml`, the other one was getting them from the `models` group. While it was possible to have two different APIs in the forms of different files for them, I chose to unify them by initialising the entry point API with the group name in its constructor (__init__) method, which gets loaded only once after the main import of the package.
This reduced the complexity of code and avoided duplication of code. The plan is also to move these entry points upstream to `PyBaMM` once they are done and tested in the `cookiecutter` template. While the `PyBaMM` project would in the future try to accommodate solvers as an entry point as well, it would be beneficial in the code base to have one single source of API to manage all the entry points.

## Summary of my contributions
- Refined `Model entry points` and made it production-ready to be merged - [PR #25](https://github.com/pybamm-team/pybamm-cookiecutter/pull/23)
- Added some workflow CI to keep track of dependencies, precisely `dependabot` - [PR #28](https://github.com/pybamm-team/pybamm-cookiecutter/pull/28)


