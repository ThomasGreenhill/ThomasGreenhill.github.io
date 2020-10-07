---
layout: post
title: System ID
date: 2020-10-07 12:06:20 +0800
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: sysid.png # Add image post (optional)
fig-caption: # Add figcaption (optional)
---
_Over the course of my summer break in 2020, I completed a System Identificaton internship with Kitty Hawk's Heaviside team. I developed a complete System ID toolkit for all phases of VTOL flight (hover, transition & forward flight). I wrote all of my code in MATLAB and based my work on [SIDPAC](https://software.nasa.gov/software/LAR-16100-1)_
* I performed system ID in both the frequency and time domains to model our aircraft's aerodynamic stability/control derivatives and come up with the aircraft's transfer functions for use in our controller's inverse plant model.
* I wrote four different simulation models, including one with non-linear and time-variant dynamics, to validate the flight test data and system ID tools.
* All in all, I developed over 100 scripts and functions to integrate system ID in our workflow, and wrote 11 documents covering the theory behind my work; all during my 10 week internship. 

**Since sharing the system ID work I performed while working for Kitty Hawk would be in violation of my NDA, I'd like to provide a brief overview of system ID and its uses instead.**

<br />
# _A Brief Overview of System ID and How It Works_
## What is System ID and Why is it Important?
_There are three fundamental aircraft dynamics and control problems:_

1. Simulation: given the input ***u*** and the system model ***s***, determine the output ***y***
1. Control: given the system model ***S*** amd the output ***y***, find the input ***u***
1. **System Identification**: given the input ***u*** and the output ***y***, find the system model ***S***

_In short, system identification involves the numerical determination of a dynamic system’s properties from a record of its response to certain inputs in the time domain. For aircraft specifically, flight test recordings are used as a basis to model dynamic behavior._

For aircraft, system ID involves performing operations on measured flight data to come up with:
* Aerodynamic coefficients to characterize performance (& control)
* Transfer functions to characterize control


System ID yields information crucial to control design: **you can't design a controller to control something without having a good idea of what you're trying to control!**

System ID is also extremely useful for the validation and calibration of design and modelling tools. **By comparing the expected performance and control of your aicraft to your aircraft's actual, measured performance and control, you can learn a lot about your modelling tools!**

***So then: where does system ID sit in the research and development feedback loop?***
![System ID in R&D]({{site.baseurl}}/assets/img/sysidrnd.png)
*Figure 1: Where System ID Sits in the R&D Feedback Loop*

## How Does System ID Actually Work?
There are many ways to perform system ID, though system ID methods are largely separated by the domains in which they operate. 
One of the most difficult parts of the system ID procedure is verifying that your identified models accurately represent the aircraft's true dynamic behavior. Each time a model is identified, a verification procedure must be used to confirm that the identified model yields responses very similar fashion to those of the actual aircraft. To complete this verification step, measured responses to measured inputs are compared to the identified plant's simulated responses to measured inputs.

<br />
The flow chart below illustrates the various stages of the system ID process along with the inputs and outputs of time domain and frequency domain system ID methods.

![Time Dom Freq Dom]({{site.baseurl}}/assets/img/freqdomtimedom.png)
*Figure 2: System ID Process Flow Chart*

## System ID In the Time Domain Using Linear Least-Squares
*Time domain system ID methods are used primarily to estimate aerodynamic stability and control coefficients (aerodynamic derivatives) using linear least-squares regression. As their name suggests, stability derivatives represent the rate of change of a force or moment quantity with respect to some perturbation quantity.*

One simple example of a stability derivative is the lift curve slope, or how the aicraft's lift coefficient (force coefficient) changes with respect to angle of attack (perturbed variable). 

In order to identify an aircraft's lift curve slope from flight test data, one must naturally evaluate the rate of change of lift coefficent with respect to angle of attack change. This can be done very efficiently using linear least squares in the time domain!

Linear least squares is a very powerful method used to approximate linear functions from several sets of data. 
Imagine a case where we wish to characterize our aircraft's lift properties by identifying its lift coefficient derivatives from the recordings of a longitudinal maneuver (like an elevator step input), using linear least squares. 
First, we must select our regressors, the quantity with which we'd like to take the derivative of lift coefficent. 

In this case, we can choose our regressors to be:
* Angle of attack
* Pitch angle 
* Elevator control deflection

Now, we can use linear least squares to estimate the rate of change of lift coefficient with respect to our regressors, leaving us with our identified derivatives! Linear least squares can also be used to calculate the steady-state value, or "bias" of a quantity, such as steady-state lift or drag. Each parameter estimate’s constant part is appended to the bias term, which represents the steady-state (trim) value of the coefficient. 

It is important to note, however, that time-domain system identification methods like the one outlined above are only useful for aircraft in forward flight. In the case of a vertical takeoff or landing (VTOL) aircraft, the scope of this type of identification is actually limited, since the aircraft spends a significant fraction of its time outside of the forward flight regime.

The figures below illustrate the result of linear least squares system identification on the simulated response of an aircraft to a 3-2-1-1 step-type input. 

<br />

![Example of Time-Domain System ID]({{site.baseurl}}/assets/img/timedom.png)
*Figure 3: Example of Time-Domain System ID*

<br />


## System ID in the Frequency Domain
Whereas time-domain system ID is useless outside of the forward flight regime, system ID can be performed in the frequency domain to determine an aircraft's transfer functions in any phase of VTOL flight. 

In order to successfully model an aircraft's behavior using frequency domain methods, sufficent frequency content must be available in the aircraft's flight recordings. 

One disadvantage to this method is the requirement of good frequency content in the flight data recordings. Without information on how an aircraft responds in the frequency domain, it is impossible to identify the system!

Transfer function system ID is extremely useful in control system design and plant modelling.