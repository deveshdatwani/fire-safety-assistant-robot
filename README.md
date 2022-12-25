# Fire safety assistant robot

<h3> This repository is to showcase my capstone exprience for Fall 2022 at Worcester Polytechnic Institute under Prof Loris Fichera. </h3>

The projcet base was define to build a robot for assisting fire fighting. For build on to this, extensive stakeholder research was carried out to identify a problem statement that has solutions in the Robotics domain.

### Stakeholder Research

Several stakeholders were engaged from different backgrounds. Worcester Fire Department & WPI Fire Safety department remained the primary and most prominent stakeholders. 

Engaging with them was extremely enlightening. I learned a great deal about fire fighting scenarious and the challenges that pertain to them. 

Identifying problem statement was the most challenging part as the stakeholders couldn't guide my team and I with finding problems that can be solved by a robot. In the Fire Department Chief's own words, "thinking out of the box" was not something they could do. Hence the onus of identifying challenges that can be solved by robots, was entirely on me and the team. 

Below our are snapshots from our engagement with the Fire Chief and pictures of the Professors we reached out to for problem statement identification.

<p align="center"><img src="https://raw.githubusercontent.com/deveshdatwani/fire-safety-assistant-robot/main/assets/firechief.jpg" height=400></p>

### Indoor Fire Safety Assistance Robot

After extensive research, it was infered that home dwellers are at maximum risk from dying in a fire incident. Below is a pie chart that illustrates fatalities during fire scenarious. A major factor is "tripping, falling" which is a surprising observation. 

To solve this, my team and I proposed a fire assistant robot that can be based off a roomba that maps the home and calculates safety scores by detecting and localizing objects along the way to the fire exit.

We proposed an additional **FIRE SAFETY STACK** for the roomba to map the indoor environment and calculate saftey scores for any indoor envornment. 

<p align="center"><img src="https://github.com/deveshdatwani/fire-safety-assistant-robot/blob/main/assets/roomba.png" width=300></p>
<p align="center"><img src="https://github.com/deveshdatwani/fire-safety-assistant-robot/blob/main/assets/robotgif.gif" width=600></p>

### The Solution

This was carried out through two methods, comparing ground truth and real time maps for detecting and locating obstacles.

This was done through a Change Detection algorithm that was original intended for remote sensing. I implemented it on cloud point data to detect obstacles and localize them in the map frame.

<p align="center"><img align="center" src="https://raw.githubusercontent.com/deveshdatwani/fire-safety-assistant-robot/main/assets/changedetection.png" width=800></p>

The CD algorithm detects changes in an image and outputs a binary image with the changes only. This is done with PCA and K Means custering on difference image obtained from ground truth map and real time map.

The Change Detection Paper can be read <a href="https://ieeexplore.ieee.org/document/5196726">here</a> 

We then used gaussian filters to evaluate safety of a room / building / floor by penalizing changes (obstacles) very close to the fire exits.   

<p align="center"><img align="center" src="https://raw.githubusercontent.com/deveshdatwani/fire-safety-assistant-robot/main/assets/riskeval.png" width=400></p>

This filter is convolved with the change map at various exit locations shown below

<p align="center"><img align="center" src="https://raw.githubusercontent.com/deveshdatwani/fire-safety-assistant-robot/main/assets/mapwithgradients.png" width=800></p>

The sum of the convolutions was mapped to fire saftey of a home. 

However, there was one issue with this, the choke points that could pose a threat to safety but were far from exits were not accounted for.  

To solve this we developed Informed RRT* algorithm from multiple locations (each room) to the exit location to find increase in path lengths to observe safety preparedness. 

We found out that increase in path lengths meant the presence of an obstacle while also indicating that it takes a longer path to safety. This could prove hazardeous in a fire emergency situation.

<p align="center"><img src="https://raw.githubusercontent.com/deveshdatwani/fire-safety-assistant-robot/main/assets/rrtbase.png" width=700></p>

### Final Product 

A combination of change detection scores and informed RRT* scores were hypothesized to calculate safety scores for fire preparedness in indoor environments. 


<p align="center"><img src="https://raw.githubusercontent.com/deveshdatwani/fire-safety-assistant-robot/main/assets/scenario1.png" width=700></p>

Home owners can be notified of possible threats to seamless evacuation during fire emergencies.

<p align="center"><img src="https://raw.githubusercontent.com/deveshdatwani/fire-safety-assistant-robot/main/assets/notify.png"></p>





