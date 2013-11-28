This is a library demonstrating the quadric fitting methods in the paper:

"Type-Constrained Direct Fitting of Quadric Surfaces" 
by James Andrews and Carlo Sequin.



BUILD INSTRUCTIONS:

Visual studio / Windows:
It should compile with the provided files "out of the box" on visual studio 2008 or higher
Be sure to compile in 'release mode' if performance matters to you!

Mac:
Just type "make".

Linux:
The makefiles were written and tested for mac, but should hopefully work on linux too.  (The makefile for the demo will likely require minor adjustments -- you will need to remove the "-framework" bits and replace them with the appropriate libraries for OpenGL.)


EXAMPLE USAGE:

See example and demo folders for examples of using the library.  Note that to build these examples you will need to build the library first (because they are set up to link against the library).


USAGE INSTRUCTIONS:

1. include "quadricfitting.h" and link against this library

2. CENTER AND RESCALE YOUR DATA! (I don't do this for you!)

3. pass the data you want to fit and a Quadric struct to one of the fit* functions, like:
void fitSphere(std::vector<data_pnw> &data, Quadric &quadric);
void fitSphere(TriangleMesh &mesh, Quadric &quadric);

If you want to fit all the quadric types at once, use one of these:
void fitAllQuadricTypes(std::vector<data_pnw> &data, std::vector<Quadric> &quadrics);
void fitAllQuadricTypes(TriangleMesh &mesh, std::vector<Quadric> &quadrics);

In both cases, the fitted quadrics are returned by reference.
If you are using one of the fitAllQuadricTypes functions, use the enumerator of quadric types to select specific quadric types -- i.e., if you want a hyperboloid, then access quadric[TYPE_HYPERBOLOID_OPT]

4. optionally use the Quadric class's member functions to help transform or render the quadric

Extra Feature: If you are fitting a quadric to a TriangleMesh, but only want to fit a specific selection of that mesh, you can use the triangleTags and activeTag members of the TriangleMesh struct.  See the comments in the TriangleMesh struct for details, and the end of aqd_example.cpp for an example of how to do this.



EXAMPLES:

The demo folder shows usage of the library with opengl to render the results.  Depends on opengl and glfw.  Press tab or arrows to change the displayed fit.

The example folder shows usage of the library without dependencies; it simply prints the quadric fits.



SUPPORT:

I'm happy to hear from anyone who is interested in using the library!
Send bug reports, feature requests, suggestions, etc, to:
zaphos@gmail.com



CAVEAT EMPTOR:

Note that this code hasn't been extensively tested.  I hope it works well as is, but let me know if there are issues and I may be able to help.