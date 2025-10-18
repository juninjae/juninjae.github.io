---
name: Auxetic Crashbox Optimization
tools: [CAD, FEA, Optimization, Experiment]
image: /assets/images/auxetic_crashbox.jpg
description: Modeling, optimizing, and experimenting with auxetic crashbox structures for improved impact energy absorption.
---

# Auxetic Crashbox Optimization

Developed and analyzed auxetic crashbox structures to enhance vehicle impact energy absorption.  
The project involved **theoretical modeling**, **multi-stage optimization (Grid Search, CMA-ES, FEA)**, and **experimental validation** using 3D-printed TPU samples.  
The optimized design achieved a **10.5% increase in energy absorption** compared to the unoptimized auxetic design, and a **53% improvement** over a hollow crashbox configuration.

**Key takeaways:**  
- Modeled auxetic unit cell behavior and derived Modulus of Resilience (MOR).  
- Optimized geometry using Grid Search, CMA-ES, and FEA to maximize energy absorption.  
- Verified performance experimentally via compression and impact testing.  

---

### Introduction
{% capture carousel_images %}
/assets/images/auxetic_crashbox/slides/slide3.JPG
/assets/images/auxetic_crashbox/slides/slide4.JPG
{% endcapture %}
{% include elements/carousel.html carousel_id="auxetic-intro" carousel_images=carousel_images %}
Crashboxes absorb low-velocity collision energy to protect the chassis. Auxetic structures with a negative Poisson’s ratio were introduced to enhance deformation efficiency and energy absorption capacity.

### Modeling
{% capture carousel_images %}
/assets/images/auxetic_crashbox/slides/slide5.JPG
/assets/images/auxetic_crashbox/slides/slide6.JPG
{% endcapture %}
{% include elements/carousel.html carousel_id="auxetic-model" carousel_images=carousel_images %}
Established mechanical and mathematical models for an auxetic “bow-tie” unit cell. Derived stress–strain relationships and calculated Modulus of Resilience (MOR) through numerical integration.

### Optimization
{% capture carousel_images %}
/assets/images/auxetic_crashbox/slides/slide7.JPG
/assets/images/auxetic_crashbox/slides/slide8.JPG
/assets/images/auxetic_crashbox/slides/slide9.JPG
/assets/images/auxetic_crashbox/slides/slide10.JPG
/assets/images/auxetic_crashbox/slides/slide11.JPG
/assets/images/auxetic_crashbox/slides/slide12.JPG
/assets/images/auxetic_crashbox/slides/slide13.JPG
/assets/images/auxetic_crashbox/slides/slide14.JPG
{% endcapture %}
{% include elements/carousel.html carousel_id="auxetic-opt" carousel_images=carousel_images %}
Performed triple-stage optimization:  
1️⃣ **Grid Search** for exhaustive parameter evaluation.  
2️⃣ **CMA-ES (Covariance Matrix Adaptation Evolution Strategy)** for adaptive optimization in multidimensional space.  
3️⃣ **Finite Element Analysis (FEA)** to verify optimized geometry and energy absorption behavior.

### Experimentation
{% capture carousel_images %}
/assets/images/auxetic_crashbox/slides/slide15.JPG
/assets/images/auxetic_crashbox/slides/slide16.JPG
/assets/images/auxetic_crashbox/slides/slide17.JPG
/assets/images/auxetic_crashbox/slides/slide18.JPG
/assets/images/auxetic_crashbox/slides/slide19.JPG
{% endcapture %}
{% include elements/carousel.html carousel_id="auxetic-exp" carousel_images=carousel_images %}
3D-printed TPU samples were tested under compression and impact using a modified tensile press and force plate.  
Results showed **10.5% higher energy absorption** for optimized auxetic inserts, and **23.1% lower peak force** on the chassis compared to hollow crashboxes.

### Appendix
{% capture carousel_images %}
/assets/images/auxetic_crashbox/slides/slide21.JPG
/assets/images/auxetic_crashbox/slides/slide22.JPG
/assets/images/auxetic_crashbox/slides/slide23.JPG
/assets/images/auxetic_crashbox/slides/slide24.JPG
/assets/images/auxetic_crashbox/slides/slide25.JPG
/assets/images/auxetic_crashbox/slides/slide26.JPG
/assets/images/auxetic_crashbox/slides/slide27.JPG
{% endcapture %}
{% include elements/carousel.html carousel_id="auxetic-appendix" carousel_images=carousel_images %}

Appendix slides summarize the theoretical and mathematical foundations behind the modeling process,  
including **beam deflection**, **stress–strain derivations**, and **Modulus of Resilience (MOR)** calculations  
used to validate the auxetic crashbox’s mechanical behavior.
