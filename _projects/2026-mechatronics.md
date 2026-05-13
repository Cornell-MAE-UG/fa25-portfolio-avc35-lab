---
layout: project
title: Mechatronics Block Collecting Robot
description: Final Proj for Mechatronics
technologies: [Schematic Drawing, Arduino, C, CAD, Circuit Design, 3D Printing]
image: /assets/images/robot.jpg
---

For MAE 3780, my team was tasked to design an autonomous robot meant to collect as many 1" blocks in 60 seconds. 
Robot Design & Overview:
We aimed to be simple in our design and strategy. Our strategy was to open ourselves up to being as wide as possible with a 3D printed claw, then to quickly collect in a simple path from one side of the middle to the other. At the start of the match, we wrote our code to open our claw, move forward until the left black border was detected, turn until the opposite color was detected, and then turn again. This allowed our robot to follow a path between the intersection of the blue and yellow section, until the black border was detected, where we would then turn right to go back to our original color section. 
For our robot, we primarily designed an L-shaped claw that would open us to the maximum legal dimensions upon start. Our claw was composed of two arms and symmetric on either side, with one long thin arm being mounted on one positional servo placed in front of our wheels. We utilized the color sensor to detect blue and yellow and two QTI sensors to detect black at the left or right side of our robot. We bought and utilized the bigger wheels from the lab to increase our speed.


[Download my final report]({{ "/assets/robotfinal.pdf" | relative_url }}) in PDF format.