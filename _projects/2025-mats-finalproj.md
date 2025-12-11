---
layout: project
title: Mechanics of Materials Final Project
description: Designing a Torque Wrench to meet Design requirements
technologies: [Autodesk Fusion, ANSYS Mechanical]
image: /assets/images/mats_final_pic.png 
---

**Our Design Results**

<u>Hand Calculations and Outputs</u> <br />
MATLAB Script is included below: <br />
%TIME TO DESIGN MY OWN <br /> 
%1mV/V output at 600 inlbf <br />
%X_Yield_strength = 4 <br />
%X_CrackGrowth = 2 is a = 0.04<br />
%X_fatigue = 1.5 <br />
%steel, al, or titanium <br />

a = 0.04; % crack length <br />
M = 600; % max torque <br />
c = 1.0; % distance from center of drive to center of strain gauge <br />

% material properties <br />
E = 17.E6; % Young's modulus psi <br />
nu = 0.37; % Poisson's ratio<br />
su = 132.E3; % tensile strength use yield or ultimate depending on material psi<br />
KIC = 97.E3; % fracture toughness psi sqrtin<br />
sfatigue = 69.e3; % fatigue strength from Granta for 10^6 cycles<br />
name = 'Ti-6Al-4V' % Ti-6Al-4V aalpha beta annealed<br />

%dimensional properties<br />
L = 16; % length from drive to where load applied (inches)<br />
h = .6; % width<br />
b = .4; % thickness <br />

%Stress and deflection analysis<br />
I = (b * h^3) / 12;<br />
sigma =  M*(h/2)/I;<br />
sigma_norm_ksi = sigma / 1000 % Convert to ksi<br />
load_point_deflection = (M * L^2) / (3 * E * I)<br />
F = M/L;<br />
Mgage = F*(L-c);<br />
sigma_g=  Mgage*(h/2)/I;<br />
k = 2;<br />
epsilon1 = sigma_g / E;<br />
epsilon2 = -epsilon1;<br />
vout_vin = k/4 * 2*epsilon1; % THIS IS CORRECT formula value<br />
strain = epsilon1/10^-3<br />
voltageOutput = vout_vin/10^-3<br />

Ki= 1.12*sigma*sqrt(pi*a);<br />
X_y_strength = su / sigma<br />
X_CrackGrowth = KIC/Ki<br />
X_Fatigue = sfatigue / abs(sigma) % Safety factor for fatigue<br />

Max normal stress: 25 ksi <br />
Deflection at Load Point: 0.4183 in <br />
Strain @ gauge: 1378.7 microstrain <br />
Yield strength FOS: 5.28 <br />
Crack Growth FOS: 9.77 <br />
Fatigue FOS: 2.76 <br />

<u> Results</u>  <br />
#1. Image(s) of CAD model. Must show all key dimensions.<br />
See the CAD image above. <br />
#2. Describe material used and its relevant mechanical properties.<br />
The material we chose was Ti-6Al-4V, a titanium alloy. We choose this material due to the strong material properties, such as a high tensile strength and high ductility. <br />

#3. Diagram communicating how loads and boundary conditions were applied to your FEM model.<br />

Torque Wrench Model in Ansys:

![Photo of FEM model]({{ "/assets/images/mats_q3.jpg" | relative_url }}){: .full_width}
<br />
#4. Normal strain contours (in the strain gauge direction) from FEM<br />
![Photo of FEM model]({{ "/assets/images/mats_q4.1.png" | relative_url }}){: .full_width}
<br />
Close-up of driver normal strain contour:
![Photo of FEM model]({{ "/assets/images/mats_q4_2.png" | relative_url }}){: .full_width}
<br />
#5. Contour plot of maximum principal stress from FEM<br />
![Photo of FEM model]({{ "/assets/images/mats_q5_1.png" | relative_url }}){: .full_width}
<br />
![Photo of FEM model]({{ "/assets/images/mats_q5_2.png" | relative_url }}){: .full_width}
<br />
#6. Summarize results from FEM calculation showing maximum normal stress (anywhere), load point deflection, strains at the strain gauge locations <br />

![Photo of FEM model]({{ "/assets/images/mats_q6_normstress.png" | relative_url }}){: .full_width}
<br />
![Photo of FEM model]({{ "/assets/images/mats_q6_strain.png" | relative_url }}){: .full_width}
<br />
Load Point Deflection: 0.503 in <br />
Strain @ gauge location: 1.4533e-003 in/in <br />
Max Normal Stress: 45.38 ksi <br />

#7. Torque wrench sensitivity in mV/V using strains from the FEM analysis <br />
Sensitivity = (strain @ gauge)* 1000 = 1.4533 mV/V <br />

#8. Strain gauge selected (give type and dimensions). Note that the design must physically have enough space to bond the gauges. <br />
Strain Gauge Selected: SGT-1LH/350-TY11 <br />
Information: Half-bridge strain gauge, 1.8 mm Grid Length, 5 mm Grid Width 350 Ω Resistance <br />
Link to selected strain gauge: https://www.dwyeromega.com/en-us/uniaxial-half-bridge-strain-gauges-with-transducer-quality/SGT-Half-Bridge-Uniaxial/p/SGT-1LH-350-TY11 <br/>
It is sensitive enough that our strain max is 30,000 µm and has a carrier length 9.2 mm and a carrier width 4 mm, this fits in our handle spot as that converted to inches is 0.36 in x 0.16 in.

