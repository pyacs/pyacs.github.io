---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.lib.icosahedron
images: {}
path: /pyacs-lib-icosahedron
title: pyacs.lib.icosahedron module
---

# pyacs.lib.icosahedron module


### pyacs.lib.icosahedron.distance(A, B)

### pyacs.lib.icosahedron.icosahedron()
Constructs an icosahedron on the unit-sphere


### pyacs.lib.icosahedron.subdivide(verts, faces)
Subdivide each triangle into four triangles, pushing verts to the unit sphere


### pyacs.lib.icosahedron.mesh_global(num_subdivisions=6)

### pyacs.lib.icosahedron.mesh_regional(num_subdivisions=6, bounds=None)
Makes an equilateral triangles mesh over a sphere of unit radius using a succesive subdivision 
of an initial icosahedron 
returns verts and faces
verts: list of vertices ; a vertice is a list of [x,y,z] in geocentric cartesian coordinates over the sphere of unit radius
faces: list of faces ; a face is a list of vertices index
faces[i][j] gives the [X, Y, Z] coordinates of vertex j of face i
