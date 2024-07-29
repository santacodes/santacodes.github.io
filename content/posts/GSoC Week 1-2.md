+++
title = 'Google Summer of Code Week 1 and 2'
date = 2024-06-29T18:59:49+05:30
categories = ["GSoC", "PyBaMM", "NumFOCUS"]
type = ["post", "posts"]
tags = ["gsoc"]
draft = false 
+++

{{< image src="https://user-images.githubusercontent.com/20817509/107091287-8ad46a80-67cf-11eb-86f5-7ebef7c72a1e.png" alt="PyBaMM" position="center" style="width:300px; border-radius: 8px;" >}}

# First week report
During the first week of my project, I had to get acquainted to the project which already had some work done to it.
The current status of the project was very minimal and wasn't usable. So I decided to start working on the project by updating licenses, code of conduct and writing a few lines of contributing guidelines just to get my hands dirty and acclimating myself with the development environment.

# Second week report
After getting my hands dirty with the previous contributions, I started setting up rules in the project. I setup `pre-commit` and added it to the CI to maintain a standard linting rule that I adopted from the `PyBaMM` project and a few auto update rules every two weeks. Later that week I updated the `README.md` of the project and added few badges and added set up procedures for the current project.

## Summary of my contributions
- Added `Code of Conduct` (contributor covenant v2.1)- [PR #10](https://github.com/pybamm-team/pybamm-cookiecutter/pull/10)
- Added tests for template generation, to ensure the generated project was the one intended to be generated. For this I used a library called `pytest-cookies` which is a wrapper for `pytest` and `cookiecutter API`- [PR #9](https://github.com/pybamm-team/pybamm-cookiecutter/pull/9)
- Added basic workflows using `github-actions` to check the `style` and `template generation` on push to the `main` branch or in a `PR` - [PR #12](https://github.com/pybamm-team/pybamm-cookiecutter/pull/12)
- Fixed style issues that were already persistent in the current code base - [PR #13](https://github.com/pybamm-team/pybamm-cookiecutter/pull/13)
