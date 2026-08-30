# The journey of a lens from the catalog to the camera
Optical design is a truly fascinating field, which combines the science of bending light with artistic thinking. It requires a fusion of precision with practicality to achieve a functioning end-product. For decades, optical design has been assisted by rigorous mathematical calculations, with softwares simplifying this process significantly over the last couple of decades. However, the field still remains esoteric and inaccessible to most people, due to not only the inherent complexity but also the high-costs associated with commercial softwares. This has posed a significant barrier for many, including students, non-academic/independent researchers and hobbyists. Thankfully, we finally have open-source tools that are sophisticated enough to rival some of the commercial software, at least for some of the simpler applications. 

This repo focuses on developing complete workflows for designing, building and testing optical systems using only open-source tools and commercial off-the-shelf components. The optical design, image-quality analysis and assembly tolerancing are modeled using **[Optiland](https://github.com/HarrisonKramer/optiland)**, an open-source optical design and simulation package for Python. Some of the image quality testing is done using **MTFMapper(https://sourceforge.net/projects/mtfmapper/)**

The lens uses two commercially available 2-inch achromatic doublets, an adjustable iris, and off-the-shelf optomechanical components to create a roughly 90 mm portrait lens for Sony APS-C mirrorless cameras.

The goal was not to reproduce the performance of a modern, highly corrected photographic lens. Instead, the design prioritizes useful central sharpness while allowing substantial off-axis aberrations to remain and contribute to the character of the image.

, 
---

## The idea

Modern photographic lenses are extraordinarily well corrected. Aberrations such as field curvature, coma, astigmatism, and chromatic aberration are generally things lens designers try to minimize.

For this project, I wanted to explore a slightly different design philosophy:

> **Make the center useful, but don't necessarily make the rest perfect.**

This is particularly interesting for portrait photography, where the subject is often close to the center of the frame and the behavior of the surrounding image can become part of the aesthetic.

Rather than designing and manufacturing custom optical elements, I wanted to see how far I could get using readily available catalog optics.

---

## Optical concept

The lens consists of two commercially available Thorlabs achromatic doublets:

* **Front group:** AC508-100-A
* **Rear group:** ACT508-300-A
* **Diameter:** 2 inches
* **Adjustable iris:** positioned between the two optical groups
* **Target effective focal length:** approximately 90 mm
* **Camera:** Sony APS-C mirrorless
* **Focusing:** movement of the front group using a helicoid

The Zemax prescriptions supplied for the catalog lenses are imported into Optiland and combined into a single optical system.

The rear achromat is reversed before the two prescriptions are combined.

---

## Designing the lens in Optiland

The design process was not limited to finding an optically favorable spacing between two lenses.

The model gradually incorporates the constraints of the lens that can actually be assembled:

* clear apertures of the catalog optics
* iris position
* inter-group spacing
* focusing helicoid travel
* SM2/M42 mechanical interfaces
* M42-to-Sony-E adapter
* Sony E-mount flange focal distance
* APS-C sensor dimensions
* mechanical apertures and potential clipping

This turns the simulation from an abstract optical prescription into a model of the physical lens.

---

## Deliberately asymmetric optimization

The optimization merit function considers **on-axis RMS spot size**.

That is intentional.

A conventional photographic-lens optimization would normally include several field positions and attempt to balance image quality across the frame. Here, the central field receives priority while the off-axis aberrations are largely allowed to evolve naturally.

The resulting aberrations are therefore not simply an optimization failure — they are part of the design objective.

Three image-height field positions are nevertheless included in the model so that the off-axis behavior can be inspected.

---

## Focusing and mechanical constraints

The physical lens uses a helicoid for focusing.

Rather than allowing the optimizer to choose arbitrary lens separations, the final optimization restricts the front-group position to the actual mechanical travel available in the assembly.

For the modeled configuration, the front-group-to-stop spacing is constrained to approximately:

**37–51 mm**

This allows the optical simulation to represent the real focusing mechanism rather than an idealized refocus operation.

---

## Image-quality analysis

Several analyses are used to understand how the unconventional design behaves.

### Through-focus spot diagrams

Through-focus spot diagrams show how the image changes around the selected focus and how quickly image quality deteriorates away from it.

### FFT MTF

FFT-based modulation transfer function calculations are performed around the selected focus position for the configured fields and wavelengths.

Rather than treating MTF as a single measure of whether the lens is "good" or "bad", it helps characterize the compromise between central resolution and the deliberately less-corrected surrounding field.

### Field curvature

Field-curvature plots are generated across the helicoid movement range.

This is particularly relevant for this design because the off-axis image surface is not forced to remain flat during optimization.

---

## What about building tolerances?

A simulation with perfectly centered and aligned lenses is not necessarily representative of a DIY optical assembly.

The catalog achromats themselves are manufactured to controlled tolerances, but mounting them in threaded tubes introduces another source of error.

The tolerance study therefore concentrates on two assembly errors:

**Tilt**

* 3σ ≈ 1°

**Decenter**

* 3σ ≈ 0.15 mm

Monte Carlo systems are generated with perturbations applied to the two achromatic groups.

The resulting changes in

* RMS spot radius
* coma
* astigmatism

are evaluated to estimate how sensitive the design is to realistic assembly errors.

Because Optiland does not currently provide direct rigid-body tilt/decenter operations for complete lens groups in this workflow, group perturbations are represented using coordinate-break-based transformations.

---

## Repository contents

The repository contains the Optiland workflow used to construct and analyze the lens.

```text
Beautifully-Aberrated/
│
├── README.md
│
├── notebooks/
│   └── DIY_Portrait_Lens_Optiland.ipynb
│
├── images/
│   └── ...
│
└── README assets / supporting files
```

The Jupyter notebook contains the complete reproducible workflow, including the optical prescription, optimization, mechanical constraints, image-quality analysis, and tolerancing.

---

## Why build an imperfect lens?

There are already countless technically excellent portrait lenses.

Trying to outperform them using two catalog achromats and threaded optomechanics would be rather optimistic.

But that isn't really the point.

This project is an experiment in using optical engineering tools for a slightly different objective: understanding which imperfections matter, which can be tolerated, and which might actually make an image more interesting.

The result sits somewhere between an optical engineering exercise and a photographic experiment.

And sometimes, a lens doesn't have to be perfectly corrected to be interesting.

---

## Tools

* Python
* Optiland
* NumPy
* Matplotlib
* Jupyter
* Zemax catalog prescriptions

---

## Status

🚧 **Work in progress**

The optical model and first-order tolerance analysis are complete. The next stages are physical characterization of the assembled lens and comparison between simulated and measured image quality.

---

## Acknowledgements

This project uses **Optiland**, the open-source Python optical design and simulation library developed by Harrison Kramer and contributors.

The optical elements are based on publicly available catalog prescriptions from Thorlabs.
