This is a C++ library that fits 3D quadric surfaces (e.g., ellipsoids, cylinders, cones, hyperboloids, spheres, etc) to a user-provided data set -- either a triangle mesh, or a set of points with normals.

Project download with source: http://jimmylands.com/allquadricsdirect.zip

This library is based on this paper: http://graphics.berkeley.edu/papers/Andrews-TCD-2013-06/index.html
Please cite the paper if you find the code useful for your research!

The library provides type-specific fitting functions, so it's designed to be especially helpful if you have an idea a-priori of the type of quadric you need the fitter to find: for example, if you know the quadric should be a sphere, or a cylinder, or a hyperbolic paraboloid, or etc, then you can specify that up-front and the library will try to find a quadric that both fits well and is of that desired quadric type.

The methods provided by this library are "direct" fitting methods, which in practice means that they are relatively fast, and do not need an 'initial guess' at the quadric parameters.  This is in contrast to iterative methods, which are typically slower and do need an initial guess.  Typically, iterative methods are more accurate, so for the best possible accuracy one may start with a direct method (like this library) and then refine it with an iterative method.  However, I find the direct method alone can often already generate reasonably accurate results.

Also included in this library is functionality to transform quadric surfaces (for example, to rotate or scale such surfaces) and to generate triangle meshes from implicit quadric forms accurately and efficiently (without relying on e.g. marching cubes).


Note that the type-specific fitting functions in this library allow fits that are "within epsilon" (or within floating point error) of the quadric type you specify.  This means that, for example, if you ask the library to fit a sphere to planar data points, the library is allowed to return a plane -- because a plane is only an infinitesimal parameter change from becoming a (very large) sphere.  I allow such "within epsilon" results because it simplifies the algorithms, and seems fine for my own applications.  If this approach causes problems for you, I'd be interested to hear about it, and potentially could update the library to optionally avoid some such "within epsilon" cases.