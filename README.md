# From the catalog to the camera
Optical design is a truly fascinating field, which combines the science of bending light with artistic thinking. It requires a fusion of precision with practicality to achieve a functioning end-product. For decades, optical design has been assisted by rigorous mathematical calculations, with softwares simplifying this process significantly over the last couple of decades. However, the field still remains esoteric and inaccessible to most people, due to not only the inherent complexity but also the high-costs associated with commercial softwares. This has posed a significant barrier for many, including students, non-academic/independent researchers and hobbyists. Thankfully, we finally have open-source tools that are sophisticated enough to rival some of the commercial software, at least for some of the simpler applications. 

This project focuses on developing a complete workflow for designing, building and testing optical systems using only open-source tools and commercial off-the-shelf components. The optical design, image-quality analysis and assembly tolerancing are modeled using **[Optiland](https://github.com/HarrisonKramer/optiland)**, an open-source optical design and simulation package for Python. Some of the image quality testing is done using **[MTFMapper](https://sourceforge.net/projects/mtfmapper/)**. Commercial off-the-shelf components already provide some room to experiment with simple combinations of lenses and optomechanics. Although they might only provide limited options for glass selection, they already a basis to excersise some creativity in component selection, wherein the constraints lead to some interesting design consequences. In the end, a variety of designs that are 'good enough' can be comfortably achieved. 

In this project, a Petzval-inspired portrait lens has been designed and built with two achromats from Thorlabs. The Jupyter notebooks contain the complete reproducible workflow, including the optical prescription, optimization, mechanical constraints, image-quality analysis and tolerancing. The sample images and the design files are included as well. 

Status

🚧 Work in progress

The optical model and first-order tolerance analysis are complete. A simple slant-edge MTF test was performed to characterize the performance of the lens. The next stages are further characterization of the assembled lens and comparison between simulated and measured image quality. Moreover, the results from simulations in Optiland will be compared to the results from Zemax OpticStudio as an attempt to benchmark Optiland.

Acknowledgements
Thanks to
1. Ronian Siew for inspiring to take up on this DIY Lens project (https://www.youtube.com/shorts/FY8pygPwD04)
2. Kramer Harrison (Optiland) for all the Optiland-related feedback and inputs
3. Christoph Jusko for kindly providing the Sony A6000 camera used in this project
