# From the Catalog to the Camera

Optical design is a fascinating field that combines the science of bending light with creative thinking. It requires a balance of precision and practicality to turn an optical concept into a functioning system. While sophisticated software has made optical design considerably more accessible, the field still remains somewhat esoteric — not only because of its inherent complexity, but also because of the high cost of commercial optical design software. This can be a significant barrier for students, independent researchers, and hobbyists.

Thankfully, increasingly capable open-source tools are beginning to lower this barrier.

This project explores a complete workflow for **designing, building, and testing an optical system using open-source tools and commercial off-the-shelf components**. The optical design, image-quality analysis, and assembly tolerancing are performed using [**Optiland**](https://github.com/HarrisonKramer/optiland), an open-source optical design and simulation package for Python. Experimental image-quality testing is also performed using [**MTF Mapper**](https://sourceforge.net/projects/mtfmapper/).

Commercial off-the-shelf optical components provide an interesting playground for this approach. Although the available glass types, curvatures, and focal lengths are constrained by the component catalog, these constraints themselves make component selection an interesting design problem. With some creativity, it is possible to arrive at optical systems that are not necessarily perfect, but are nevertheless *good enough* for their intended purpose.

As a demonstration, I designed and built a **Petzval-inspired portrait lens using two catalog achromats from Thorlabs**. The Jupyter notebooks in this repository contain the reproducible workflow, including the optical prescription, optimization, mechanical constraints, image-quality analysis, and assembly tolerancing. Sample photographs and relevant design files are also included.

## Status

🚧 **Work in progress**

The optical model and first-order tolerance analysis are complete, and a simple slant-edge MTF measurement has been performed to characterize the assembled lens.

The next steps are further experimental characterization and a comparison between simulated and measured image quality. The Optiland simulation results will also be compared with results from Zemax OpticStudio as a small benchmark of the open-source workflow.

## Acknowledgements

Thanks to:

1. **Ronian Siew**, who inspired me to try building one myself ([video](https://www.youtube.com/shorts/FY8pygPwD04)).
2. **Kramer Harrison**, developer of Optiland, for his feedback and input on Optiland-related questions.
3. **Christoph Jusko**, for kindly providing the Sony A6000 camera used in this project.
