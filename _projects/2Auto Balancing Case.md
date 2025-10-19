---
name: Auto Balancing Case
tools: [Arduino, CAD, Reinforcement Learning, Sim2Real]
image: /assets/images/ABC.png
description: A smart suitcase that automatically shifts its center of mass to reduce wrist load and maintain balance across uneven surfaces.
---

# Auto Balancing Case

![Auto Balancing Case](/assets/images/ABC.png)

An **auto-balancing suitcase** that dynamically adjusts its center of mass to reduce wrist torque and **improve user comfort** on uneven surfaces.  
Developed through an end-to-end pipeline, covering hardware fabrication, sensing, reinforcement learning, Sim2Real transfer, and real-time control.  
All design files, simulation environments, and reinforcement learning policies are fully open-sourced.  
[🔗 Source Code](https://github.com/erickun0125/Auto_Balancing_Case)

{% include elements/video.html video_ids="2wkL5crLkIA" %}

---

### Problem & Motivation
{% include elements/figure.html image="/assets/images/ABC/slides/slide1.jpg" %}

Conventional suitcases often tilt forward on carpets, ramps, and uneven surfaces, **requiring users to apply excessive wrist torque** to maintain posture.  
As suitcase use increases with frequent travel and long-distance mobility, the demand for reduced user fatigue and improved handling comfort continues to grow.  
Unlike existing autonomous suitcases that rely on costly and complex vision based SLAM systems, this project focuses on automating posture stabilization-allowing users to simply push the suitcase without exerting extra wrist effort.  


### Solution Concept
{% include elements/figure.html image="/assets/images/ABC/slides/slide2.jpg" %}

Introduced a **mass-shifting upper body** design that moves the luggage’s center of gravity rearward during pushing.  
By preventing initial tipping, the design eliminates the need for users to apply wrist torque to maintain balance.  
Unlike complex self-driving suitcases, this design maintains simplicity while enhancing ergonomic comfort and stability.  


### Hardware Development
{% capture carousel_images %}
/assets/images/ABC/slides/hardware1.png
/assets/images/ABC/slides/hardware2.png
{% endcapture %}
{% include elements/carousel.html carousel_id="abc-hw" carousel_images=carousel_images %}

#### Sensor Design  
- Four **button-type load cells** mounted at each wheel measure ground contact load.  
- Two **bar-type load cells** in the handle measure user-applied forces.  
- All signals are amplified via **HX711 modules** for precise data acquisition.  

#### Actuator Design  
- Dual **Dynamixel XL430-W250-T** motors connected via a **differential gear** to generate a single controlled tilt angle.  
- Base structure remains in continuous contact with the ground, minimizing axial load on the actuators.


### Reinforcement Learning
{% capture carousel_images %}
/assets/images/ABC/slides/rl1.png
{% endcapture %}
{% include elements/carousel.html carousel_id="abc-rl" carousel_images=carousel_images %}

- **Simulation Environment:** Built using NVIDIA PhysX-based **Isaac Sim** with custom CAD-to-URDF/USD modeling.  
- **Framework:** NVIDIA Isaac Lab + RSL-RL Agent (PPO Runner).  
- **Training Strategy:** Domain Randomization + Custom Reward (posture stability, balanced wheel loads).  
- **Outcome:** Learned robust control policies for balancing under disturbances and slope conditions.


### Sim2Real Transfer
{% capture carousel_images %}
/assets/images/ABC/slides/sim2real1.png
{% endcapture %}
{% include elements/carousel.html carousel_id="abc-sim2real" carousel_images=carousel_images %}

- **Sensor Interface:** Real-time load sensing via Arduino + HX711.  
- **Motor Control:** Low-level actuation with Dynamixel SDK.  
- **Policy Integration:** Simulation-trained control policies adapted to hardware through a custom I/O bridge.  
- **Gap Mitigation:** Addressed delay, noise, and frequency mismatches for stable real-world transfer.


### Control Loop
{% capture carousel_images %}
/assets/images/ABC/slides/control1.png
{% endcapture %}
{% include elements/carousel.html carousel_id="abc-control" carousel_images=carousel_images %}

The RL-based controller operates at **50 Hz**, continuously reading sensor inputs, running the learned policy, and outputting real-time motor commands.  
This feedback loop maintains upright stability during start, stop, and uneven-surface transitions.


### Results
{% capture carousel_images %}
/assets/images/ABC/slides/result1.png
/assets/images/ABC/slides/result2.png
{% endcapture %}
{% include elements/carousel.html carousel_id="abc-result" carousel_images=carousel_images %}

- **Successfully maintained stability** on slopes and rough terrains without additional user torque.  
- Demonstrated **smooth center-of-mass adjustment** and responsive recovery during external disturbances.  
- The modular design can be **embedded into existing suitcase frames**, allowing scalable manufacturing and product integration.


### Future Work
Potential extensions include integrating **IMU-based posture estimation**, adaptive control for dynamic walking scenarios, and expanded application to **carts and logistics platforms**.


### Appendix
{% capture carousel_images %}
/assets/images/ABC/slides/appendix1.png
/assets/images/ABC/slides/appendix2.png
{% endcapture %}
{% include elements/carousel.html carousel_id="abc-appendix" carousel_images=carousel_images %}
Additional diagrams and control flowcharts illustrating the system architecture and policy pipeline.
