+++
title = 'Google Summer of Code Week 5 and 6'
date = 2024-06-29T18:59:49+05:30
categories = ["GSoC", "PyBaMM", "NumFOCUS"]
type = ["post", "posts"]
tags = ["gsoc"]
draft = false 
+++

{{< image src="https://user-images.githubusercontent.com/20817509/107091287-8ad46a80-67cf-11eb-86f5-7ebef7c72a1e.png" alt="PyBaMM" position="center" style="width:300px; border-radius: 8px;" >}}

# Fifth and sixth week report
After I got the `entry points` for parameter sets working, it was time for `Model entry points`. If you haven't read about my previous blog post on parameter entry points, you can read it [here]({{< ref "GSoC Week 3-4.md" >}}).

## What are Model entry points?
Just like adding a third-party parameter set, you could even add your own models to a python package to be accessed using PyBaMM. PyBaMM has a set of predifined models in its own module like the `BasicSPM`. Let us say just like a third-party parameter set, a user wants to add their own model without actually adding it to the PyBaMM

