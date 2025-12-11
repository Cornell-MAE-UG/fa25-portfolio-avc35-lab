---
layout: project
title: Mechanics of Materials Final Project
description: Designing a Torque Wrench to meet Design requirements
technologies: [Autodesk Fusion, ANSYS Mechanical]
image: /assets/images/mats_final_pic.png
---

**Our Design Results**

<u>Hand Calculations and Outputs</u> 
MATLAB Script is included below: <br />
%TIME TO DESIGN MY OWN
%1mV/V output at 600 inlbf
%X_Yield_strength = 4 
%X_CrackGrowth = 2 is a = 0.04
%X_fatigue = 1.5
%steel, al, or titanium

a = 0.04; % crack length
M = 600; % max torque
c = 1.0; % distance from center of drive to center of strain gauge

% material properties
E = 17.E6; % Young's modulus psi
nu = 0.37; % Poisson's ratio
su = 132.E3; % tensile strength use yield or ultimate depending on material psi
KIC = 97.E3; % fracture toughness psi sqrtin
sfatigue = 69.e3; % fatigue strength from Granta for 10^6 cycles
name = 'Ti-6Al-4V' % Ti-6Al-4V aalpha beta annealed

%dimensional properties
L = 16; % length from drive to where load applied (inches)
h = .6; % width
b = .4; % thickness

%Stress and deflection analysis
I = (b * h^3) / 12;
sigma =  M*(h/2)/I;
sigma_norm_ksi = sigma / 1000 % Convert to ksi
load_point_deflection = (M * L^2) / (3 * E * I)
F = M/L;
Mgage = F*(L-c);
sigma_g=  Mgage*(h/2)/I;
k = 2;
epsilon1 = sigma_g / E;
epsilon2 = -epsilon1;
vout_vin = k/4 * 2*epsilon1; % THIS IS CORRECT formula value
strain = epsilon1/10^-3
voltageOutput = vout_vin/10^-3

Ki= 1.12*sigma*sqrt(pi*a);
X_y_strength = su / sigma
X_CrackGrowth = KIC/Ki
X_Fatigue = sfatigue / abs(sigma) % Safety factor for fatigue

Max normal stress: 25 ksi <br />
Deflection at Load Point: 0.4183 in <br />
Strain @ gauge: 1378.7 microstrain <br />
Yield strength FOS: 5.28 <br />
Crack Growth FOS: 9.77 <br />
Fatigue FOS: 2.76 <br />

Results
1. Image(s) of CAD model. Must show all key dimensions.
See the CAD image above. 
2. Describe material used and its relevant mechanical properties.
The material we chose was Ti-6Al-4V, a titanium alloy. We choose this material due to the strong material properties, such as a high tensile strength and high ductility. 
3. Diagram communicating how loads and boundary conditions were applied to your FEM model.

Torque Wrench Model in Ansys:

![Photo of FEM model]({{ "/assets/images/mats_q3.jpg" | relative_url }}){: .inline-image-l}

4. Normal strain contours (in the strain gauge direction) from FEM


