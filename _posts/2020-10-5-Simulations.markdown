---
layout: post
title: Simulation Models
date: 2020-10-05 13:30:20 +0800
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: blockdiag.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
---
_Over the course of the last two years, I have coded many different simulation models to evaluate the behavior of various dynamic systems. My experience writing simulation models spans from very simple linear, time-invariant models to time-variant models with non-linear kinematics. The most involved simulation I've coded to-date involved non-linear kinematics and recursive calls to [AVL](http://web.mit.edu/drela/Public/web/avl/), using python to create a high-fidelity simulation model for flight regimes greatly disturbed from trimmed flight._ 

## Flight Dynamics Simulation Visualization Using MATLAB
_Earlier this year, I wrote a 6-DOF linear, time invariant flight simulation model and visualization suite in MATLAB which takes any of four inputs (elevator, thrust, aileron, rudder) and simulates the outputs in time. This simulation uses linear kinematics and euler angles, so it only accurately models flight dynamics with small perturbations around the trim coniditon (though giving it inputs that discrupt greatly from trim certainly makes for a cool animation!). The aircraft's stability and control derivatives can be very easily adjusted to accurately reflect the behavior of the aircraft of your choice!_


![Response to Elevator Input]({{site.baseurl}}/assets/img/de_simulation_animation.gif)
*6DOF Response to an Elevator Step-Doublet* <br />


![Response to Rudder Input]({{site.baseurl}}/assets/img/dr_simulation_animation.gif)
*6DOF Response to a Rudder Step* <br />

![Response to Aileron Input]({{site.baseurl}}/assets/img/da_simulation_animation.gif)
*6DOF Response to an Aileron Step-Doublet*

![Response to MIMO Input]({{site.baseurl}}/assets/img/MIMO_simulation_animation.gif)
*6DOF Response to Multiple Inputs*
