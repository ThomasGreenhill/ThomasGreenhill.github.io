---
layout: post
title: System ID
date: 2020-10-05 12:06:20 +0800
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: sysid.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
---
_Over the course of my summer break in 2020, I completed a System Identificaton internship with Kitty Hawk's Heaviside team. I developed a complete System ID toolkit for all phases of VTOL flight (hover, transition & forward flight). I wrote all of my code in MATLAB and based my work on [SIDPAC](https://software.nasa.gov/software/LAR-16100-1)_
* I performed system ID in both the frequency and time domains to model our aircraft's aerodynamic stability/control derivatives and come up with the aircraft's transfer functions for use in our controller's inverse plant model.
* I wrote four different simulation models, including one with non-linear and time-variant dynamics, to validate the flight test data and system ID tools.
* All in all, I developed over 100 scripts and functions, and wrote 11 documents covering the theory behind my work; all during my 10 week internship. 

_A brief overview of how system ID is performed in the time and frequency domains._
## System ID In the Time Domain Using Linear Least-Squares
*Time domain system ID works by estimating a real parameter vector with a standard model such that the measured output matches the 
First, the maneuver of interest must be selected. The flight log snippet endpoints can be tuned to improve the modelling of individual coefficients (e.g. tight bounds on the maneuver for good XX_(δ_e )(control power) coefficient approximation; wide bounds on the maneuver for good XX_0 (steady state) coefficient approximation).
<br />
Next, the non-dimensional lift and drag force coefficients and the X and Z body axes force coefficients must be produced in order to perform system identification with respect to those forces. Similarly, the non-dimensional pitch moment coefficient must be produced for pitching moment derivative identification. A set of regressors (perturbed variables) is chosen to perform the system identification. It is important to choose a set of regressors which exhibit an adequate amplitude over the course of the flight test sample as to ensure that the relationships between perturbations and outputs are conditioned satisfactorily for the system identification tools. In this case, the perturbed variables chosen are angle of attack and elevator deflection. Additional perturbed variables that could be considered are angle of attack rate, non-dimensional pitch rate and airspeed; so long that the recordings of these variables exhibit substantial changes throughout the maneuver. Each parameter estimate’s constant part is appended to the bias term, which represents the steady-state (trim) value of the coefficient. 
<br />
![Example of Time-Domain System ID]({{site.baseurl}}/assets/img/timedom.jpg)
*Example of Time-Domain System ID* <br />


## System ID in the Frequency Domain