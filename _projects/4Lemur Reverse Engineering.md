---
name: FCX24 Lemur - Reverse Engineering and Improvement
tools: [Modeling, Simulation, Dynamics]
image: /assets/images/FCX24.png
description: Reverse engineering, dynamic analysis, and performance improvement of the FCX24 Lemur RC Car; for better stability and traction.
---

# FCX24 Lemur – Reverse Engineering and Improvement
{% include elements/figure.html image="/assets/images/FCX24.png" %}
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
/assets/images/Lemur/slides/slide4.JPG
/assets/images/Lemur/slides/slide5.JPG
/assets/images/Lemur/slides/slide6.JPG
{% endcapture %}
{% include elements/carousel.html carousel_id="lemur-intro" carousel_images=carousel_images %}
Analyzed the FCX24 Lemur RC car to understand real-vehicle dynamics using an accessible small-scale platform.

### Analysis
Conducted structural and dynamic analysis on chassis, suspension, steering, and drivetrain using CAD and simulation.

#### Chassis
{% capture carousel_images %}
/assets/images/Lemur/slides/slide7.JPG
/assets/images/Lemur/slides/slide8.JPG
{% endcapture %}
{% include elements/carousel.html carousel_id="lemur-chassis" carousel_images=carousel_images %}
Simulated horizontal and vertical loads in Fusion 360 and ANSYS; chassis withstood > 250 N vertically with minimal deformation.

#### Suspension
{% capture carousel_images %}
/assets/images/Lemur/slides/slide9.JPG
/assets/images/Lemur/slides/slide10.JPG
/assets/images/Lemur/slides/slide11.JPG
{% endcapture %}
{% include elements/carousel.html carousel_id="lemur-suspension" carousel_images=carousel_images %}
Modeled spring–damper behavior and measured stiffness/damping values (k₁ = 2141 N/m, c₀ = 20 Ns/m) for optimal ride stability.

#### Steering & Drivetrain
{% capture carousel_images %}
/assets/images/Lemur/slides/slide12.JPG
/assets/images/Lemur/slides/slide13.JPG
/assets/images/Lemur/slides/slide14.JPG
/assets/images/Lemur/slides/slide15.JPG
/assets/images/Lemur/slides/slide16.JPG
/assets/images/Lemur/slides/slide17.JPG
/assets/images/Lemur/slides/slide18.JPG
/assets/images/Lemur/slides/slide19.JPG
{% endcapture %}
{% include elements/carousel.html carousel_id="lemur-drivetrain" carousel_images=carousel_images %}
Calculated gear ratios and torque multipliers (22.3× low-gear vs 6.7× high-gear); confirmed inverse relation between speed and torque.

### Improvement
{% capture carousel_images %}
/assets/images/Lemur/slides/slide20.JPG
/assets/images/Lemur/slides/slide21.JPG
/assets/images/Lemur/slides/slide22.JPG
{% endcapture %}
{% include elements/carousel.html carousel_id="lemur-improvement" carousel_images=carousel_images %}
Tested fabricated improvements, including a rear-biased suspension with custom-viscosity oil (2010 cSt) designed to reduce wheel slip and enhance traction.

### Report
{% assign report_path = "/assets/publications/FCX24 Lemur.pdf" %}
<iframe 
  src="{{ report_path | relative_url }}" 
  style="width:100%; height:90vh; border:none;" 
  title="FCX24 Lemur Report PDF">
</iframe>
