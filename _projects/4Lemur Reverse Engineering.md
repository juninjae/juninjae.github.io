---
name: FCX24 Lemur - Reverse Engineering and Improvement
tools: [CAD, Mechanism Design, Simulation, Dynamics]
image: /assets/images/Lemur thumbnail.png
description: Reverse engineering, dynamic analysis, and performance improvement of the FCX24 Lemur RC Car —  for better stability and traction.
---

# FCX24 Lemur – Reverse Engineering and Improvement

This project involved **complete disassembly, 3D modeling, and mechanical analysis** of the FMS FCX24 Lemur 1:24 RC Car.  
The work included detailed studies of its **chassis, drivetrain, suspension, and steering systems** using Fusion 360 and ANSYS to explore real automotive dynamics on a miniature scale.
Finally, to prevent rear-wheel slip our team designed and tested a **custom-damped suspension**.

**Key takeaways:**  
- Achieved 3.3× torque difference between gears via two-speed transmission analysis.  
- Verified chassis strength (>250 N vertical load capacity) and impact safety through simulation.  
- Designed and validated a new damper (18 Ns/m) reducing slip and improving traction under incline conditions.  

---

### Introduction
{% capture carousel_images %}
/assets/images/Lemur/slides/슬라이드4.jpg
/assets/images/Lemur/slides/슬라이드5.jpg
/assets/images/Lemur/slides/슬라이드6.jpg
{% endcapture %}
{% include elements/carousel.html carousel_id="carousel2" carousel_images=carousel_images %}
Analyzed the FCX24 Lemur RC car to understand real-vehicle dynamics using an accessible small-scale platform.

### Analysis
Conducted structural and dynamic analysis on chassis, suspension, steering, and drivetrain using CAD and simulation.

#### Chassis
{% capture carousel_images %}
/assets/images/Lemur/slides/슬라이드7.jpg
/assets/images/Lemur/slides/슬라이드8.jpg
{% endcapture %}
{% include elements/carousel.html carousel_id="carousel2" carousel_images=carousel_images %}
Simulated horizontal and vertical loads in Fusion 360 and ANSYS; chassis withstood > 250 N vertically with minimal deformation.

#### Suspension
{% capture carousel_images %}
/assets/images/Lemur/slides/슬라이드9.jpg
/assets/images/Lemur/slides/슬라이드10.jpg
/assets/images/Lemur/slides/슬라이드11.jpg
{% endcapture %}
{% include elements/carousel.html carousel_id="carousel2" carousel_images=carousel_images %}
Modeled spring–damper behavior and measured stiffness/damping values (k₁ = 2141 N/m, c₀ = 20 Ns/m) for optimal ride stability.

#### Steering & Drivetrain
{% capture carousel_images %}
/assets/images/Lemur/slides/슬라이드12.jpg
/assets/images/Lemur/slides/슬라이드13.jpg
/assets/images/Lemur/slides/슬라이드14.jpg
/assets/images/Lemur/slides/슬라이드15.jpg
/assets/images/Lemur/slides/슬라이드16.jpg
/assets/images/Lemur/slides/슬라이드17.jpg
/assets/images/Lemur/slides/슬라이드18.jpg
/assets/images/Lemur/slides/슬라이드19.jpg
{% endcapture %}
{% include elements/carousel.html carousel_id="carousel2" carousel_images=carousel_images %}
Calculated gear ratios and torque multipliers (22.3× low-gear vs 6.7× high-gear); confirmed inverse relation between speed and torque.

### Improvement
{% capture carousel_images %}
/assets/images/Lemur/slides/슬라이드20.jpg
/assets/images/Lemur/slides/슬라이드21.jpg
/assets/images/Lemur/slides/슬라이드22.jpg
{% endcapture %}
{% include elements/carousel.html carousel_id="carousel2" carousel_images=carousel_images %}
Tested fabricated improvements, including a rear-biased suspension with custom-viscosity oil (2010 cSt) designed to reduce wheel slip and enhance traction.


