# The power of modularity in open-source

> Dieter Werthmüller (1,2), Seogi Kang (3), Thomas Günther (4), Wouter Deleersnyder (5,6), María Carrizo Mascarell (2,7), and Lukas Aigner (8).
> 1. ETH Zurich, Switzerland
> 2. TU Delft, The Netherlands
> 3. University of Manitoba, Canada
> 4. TU Bergakademie Freiberg, Germany
> 5. The University of British Columbia, Canada
> 6. KU Leuven, Belgium
> 7. Seekable, The Netherlands
> 8. TU Wien, Austria

The advantages open-source projects which are well-documented and modularly-designed starts to really shine when they allow to combine different tools to create new possibilities. We have achieved this in the last few years within the electromagnetic (EM) geophysics community.

PyGIMLi is an open-source library for multi-method modelling and inversion in geophysics. It is particularly strong in electrical resistivity tomography, induced polarization, magnetics, and seismic refraction and traveltime tomography. It is also strong in joint inversions. However, it cannot, as of now, conduct an electromagnetic modelling.

SimPEG is an open-source Python package for simulation and gradient based parameter estimation in geophysical applications. It provide strong capabilities  particularly for modelling gravity, magnetics, direct current resistivity, induced polarization, and also frequency- and time-domain electromagnetic data. Additinoal it provide a joint inversion capability. However, the analytical 1D forward modelling is, currently, limited to loop-loop configurations. Further, for a 3D EM modeling, it uses a direct solver requring a large memmory.

The emsig project contains a bunch of different codes. One of them is empymod, which is a semi-analytical electromagnetic code for layered media that can model any source and receiver configuration. Another one is emg3d, a three-dimensional modeller for EM diffusion. It provides a matrix-free multigrid solver, which means that it has a comparatively low memory footprint. However, both of these codes are purely forward modelling codes, and contain no possibility for inversions.

We will present how these codes can be combined to use the forward modelling capabilities of emsig, together with the inversion capabilities of SimPEG and pyGIMli. This not only elevates all codes to create new things in the form of SimPEG(emsig) and pyGIMLi(emsig), but more importantly, it also allows to compare different frameworks to each other. While doing these exercises we did come across struggles, concepts that have to be modularized better and be improved in the future. In particular, forward modelling codes should be able to provide easy ways to get the forward response as well as the (adjoint-state of analytical) gradient. Inversion codes, on the other hand, should be able to run the inversion without the knowledge of survey configuration or any of the underlying method, just with the forward responses and the gradients. These are ideas which are often not thought of when starting a new project, but it would make life much easier if it were.
