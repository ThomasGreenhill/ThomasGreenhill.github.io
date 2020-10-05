---
layout: post
title: Dynamics & Control
date: 2020-10-05 07:30:20 +0800
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: Hinf.jpg # Add image post (optional)
fig-caption:  caption # Add figcaption (optional)
tags: [Control, System Dynamics, Mechatronics]
---
_Over the last year or so, I have become infatuated with system dynamics, stability and control; particularly as they relate to aircraft. I have pushed myself to take graduate-level controls courses and have written several reports relating to dynamics and control of aircraft. Over the 2020 summer, I completed a System Identificaton internship with Kitty Hawk's Heaviside team._
<br /><br />

_After I complete my undergraduate eduction, I plan to pursue a masters or PhD degree in control systems/mechatronics_

## Flight Dynamics Simulation Visualizations
_I wrote a 6-DOF linear, time invariant flight simulation model and visualizer in MATLAB which takes any of four inputs (elevator, thrust, aileron, rudder) and simulates the outputs in time. This simulation uses linear kinematics and euler angles, so it only accurately models flight dynamics with small perturbations around the trim coniditon (though giving it inputs that discrupt greatly from trim does make for a cool animation!)._


<!-- ![Response to Elevator Input]({{site.baseurl}}/assets/img/de_simulation_animation.gif) -->
*Aircraft Response to an Elevator Step-Doublet* <br />

<!-- ![Response to Rudder Input]({{site.baseurl}}/assets/img/dr_simulation_animation.gif) -->
*Aircraft Response to a Rudder Step* <br />

![Response to Aileron Input]({{site.baseurl}}/assets/img/da_simulation_animation.gif)
*Aircraft Response to an Aileron Step-Doublet*

<!-- ![Response to Aileron Input]({{site.baseurl}}/assets/img/MIMO_simulation_animation.gif) -->
*Aircraft Response to Multiple Inputs*

## C-5A Galaxy
Over the last year, I have written two reports on the C-5A galaxy to evaluate its handling qualities and control. 

### An Evaluation of the C-5A's Longitudinal Performance, Control & Handling Qualities
<object data="{{site.baseurl}}/assets/pdf/C5-Handling-Control.pdf" width="600" height="600" type='application/pdf'></object>

### Designing MIMO Controllers to Improve the C-5A's Handling Qualities Using Youla Parameterization and Optimal Control Techniques
<object data="{{site.baseurl}}/assets/pdf/C5-MIMO-Control.pdf" width="600" height="600" type='application/pdf'></object>

## System ID for Aircraft