+++
title = 'Google Summer of Code Community Bonding - PyBaMM under NumFOCUS'
date = 2024-05-29T18:59:49+05:30
draft = false 
+++

{{< image src="https://user-images.githubusercontent.com/20817509/107091287-8ad46a80-67cf-11eb-86f5-7ebef7c72a1e.png" alt="PyBaMM" position="center" style="width:500px; border-radius: 8px;" >}}

## Introduction 
This is the first blog of a series of 6 blogs that I will be writing throughout every two weeks of Google Summer of Code (GSoC). My [proposal](https://summerofcode.withgoogle.com/programs/2024/projects/eU9Jznmr) got accepted under the parent organistaion [NumFOCUS](https://numfocus.org/) and sub-organisation [PyBaMM](https://www.pybamm.org/).

## About my organisation PyBaMM
PyBaMM (Python Battery Mathematical Modeling) is an open-source python module for the simulation of battery models. PyBaMM aims to provide a flexible, user-friendly, and high-performance platform for researchers, engineers, and developers working in the field of battery modeling and electrochemical simulations.
It provides inbuilt battery models and parameter sets to visualise, simulate and analyse the overall interpretability of a battery model.

## About my project
My project under PyBaMM in GSoC-2024 is a medium sized project (175 hours) and it aims to **build and publish PyBaMM-cookiecutter as a template for new PyBaMM-based projects**. A cookiecutter template is designed to simplify the setup process of the development environment for researchers and scientists interested in utilizing PyBaMM for battery modeling who may lack familiarity with managing Python environments or repositories. The project intends to enhance the accessibility and usability of PyBaMM for newbies and experienced users alike. Providing a standardized template with best practices and automation tools would lower the barrier to entry for adopting PyBaMM in battery modeling projects. This would in turn make battery modeling more accessible, efficient, and collaborative for the research community. The project also intends to implement **Model entry points**, allowing community contributors to create and share models of their repositories using the cookiecutter template without directly adding them upstream. This would not only let community contributors retain ownership and choose license terms but also grant flexibility to the PyBaMM team in supporting models, Including all of GitHub's functionality and infrastructure contained within the template.

## Contributions 
During the community bonding period, I tackled some of the listed issues, before the acceptance of my proposal I worked on development docker images of pybamm ([PR](https://github.com/pybamm-team/PyBaMM/pull/3901)) which further led me to work on some tweaks in the docker linux environment and fix the permissions and roles of a user ([PR](https://github.com/pybamm-team/PyBaMM/pull/3947)). Later I worked on docker releases and reduced the number of multi-platform docker images to just one ([PR](https://github.com/pybamm-team/PyBaMM/pull/3992)) and worked on hosting the data of pybamm results in a seperate repository and only fetching them whenever needed to reduce the whl size of the overall package ([PR](https://github.com/pybamm-team/PyBaMM/pull/4098)). 

## Footnotes
I am grateful for this opportunity and really excited to work on my project and I am thrilled to be mentored by [Saransh Chopra](https://github.com/Saransh-cpp), [Agriya Khetarpal](https://github.com/agriyakhetarpal), [Ferran Brosaplanella](https://github.com/https://github.com/brosaplanella), and [Arjun Verma](https://githuc.com/arjxn-py). 
