---
date: '2020-10-02T17:56:24.758Z'
docname: pyacs.lib.euclid
images: {}
path: /pyacs-lib-euclid
title: pyacs.lib.euclid module
---

# pyacs.lib.euclid module

euclid graphics maths module

Documentation and tests are included in the file “euclid.rst”, or online
at [https://github.com/ezag/pyeuclid/blob/master/euclid.rst](https://github.com/ezag/pyeuclid/blob/master/euclid.rst)


### class pyacs.lib.euclid.Vector2(x=0, y=0)
Bases: `object`


#### x()

#### y()

#### copy()

#### magnitude()

#### magnitude_squared()

#### normalize()

#### normalized()

#### dot(other)

#### cross()

#### reflect(normal)

#### angle(other)
Return the angle to the vector other


#### project(other)
Return one vector projected on the vector other


### class pyacs.lib.euclid.Vector3(x=0, y=0, z=0)
Bases: `object`


#### x()

#### y()

#### z()

#### copy()

#### magnitude()

#### magnitude_squared()

#### normalize()

#### normalized()

#### dot(other)

#### cross(other)

#### reflect(normal)

#### rotate_around(axis, theta)
Return the vector rotated around axis through angle theta. Right hand rule applies


#### angle(other)
Return the angle to the vector other


#### project(other)
Return one vector projected on the vector other


### class pyacs.lib.euclid.Matrix3()
Bases: `object`


#### copy()

#### identity()

#### scale(x, y)

#### translate(x, y)

#### rotate(angle)

#### classmethod new_identity()

#### classmethod new_scale(x, y)

#### classmethod new_translate(x, y)

#### classmethod new_rotate(angle)

#### determinant()

#### inverse()

#### a()

#### b()

#### c()

#### e()

#### f()

#### g()

#### i()

#### j()

#### k()

### class pyacs.lib.euclid.Matrix4()
Bases: `object`


#### copy()

#### transform(other)

#### identity()

#### scale(x, y, z)

#### translate(x, y, z)

#### rotatex(angle)

#### rotatey(angle)

#### rotatez(angle)

#### rotate_axis(angle, axis)

#### rotate_euler(heading, attitude, bank)

#### rotate_triple_axis(x, y, z)

#### transpose()

#### transposed()

#### classmethod new(\*values)

#### classmethod new_identity()

#### classmethod new_scale(x, y, z)

#### classmethod new_translate(x, y, z)

#### classmethod new_rotatex(angle)

#### classmethod new_rotatey(angle)

#### classmethod new_rotatez(angle)

#### classmethod new_rotate_axis(angle, axis)

#### classmethod new_rotate_euler(heading, attitude, bank)

#### classmethod new_rotate_triple_axis(x, y, z)

#### classmethod new_look_at(eye, at, up)

#### classmethod new_perspective(fov_y, aspect, near, far)

#### determinant()

#### inverse()

#### get_quaternion()
Returns a quaternion representing the rotation part of the matrix.
Taken from:
[http://web.archive.org/web/20041029003853/http://www.j3d.org/matrix_faq/matrfaq_latest.html#Q55](http://web.archive.org/web/20041029003853/http://www.j3d.org/matrix_faq/matrfaq_latest.html#Q55)


#### a()

#### b()

#### c()

#### d()

#### e()

#### f()

#### g()

#### h()

#### i()

#### j()

#### k()

#### l()

#### m()

#### n()

#### o()

#### p()

### class pyacs.lib.euclid.Quaternion(w=1, x=0, y=0, z=0)
Bases: `object`


#### w()

#### x()

#### y()

#### z()

#### copy()

#### magnitude()

#### magnitude_squared()

#### identity()

#### rotate_axis(angle, axis)

#### rotate_euler(heading, attitude, bank)

#### rotate_matrix(m)

#### conjugated()

#### normalize()

#### normalized()

#### get_angle_axis()

#### get_euler()

#### get_matrix()

#### classmethod new_identity()

#### classmethod new_rotate_axis(angle, axis)

#### classmethod new_rotate_euler(heading, attitude, bank)

#### classmethod new_rotate_matrix(m)

#### classmethod new_interpolate(q1, q2, t)

### class pyacs.lib.euclid.Geometry()
Bases: `object`


#### intersect(other)

#### connect(other)

#### distance(other)

### class pyacs.lib.euclid.Point2(x=0, y=0)
Bases: `pyacs.lib.euclid.Vector2`, `pyacs.lib.euclid.Geometry`


#### intersect(other)

#### connect(other)

#### x()

#### y()

### class pyacs.lib.euclid.Line2(\*args)
Bases: `pyacs.lib.euclid.Geometry`


#### p()

#### v()

#### copy()

#### property p1()

#### property p2()

#### intersect(other)

#### connect(other)

### class pyacs.lib.euclid.Ray2(\*args)
Bases: `pyacs.lib.euclid.Line2`


#### p()

#### v()

### class pyacs.lib.euclid.LineSegment2(\*args)
Bases: `pyacs.lib.euclid.Line2`


#### magnitude_squared()

#### property length()

#### p()

#### v()

### class pyacs.lib.euclid.Circle(center, radius)
Bases: `pyacs.lib.euclid.Geometry`


#### c()

#### r()

#### copy()

#### intersect(other)

#### connect(other)

#### tangent_points(p)

### class pyacs.lib.euclid.Point3(x=0, y=0, z=0)
Bases: `pyacs.lib.euclid.Vector3`, `pyacs.lib.euclid.Geometry`


#### intersect(other)

#### connect(other)

#### x()

#### y()

#### z()

### class pyacs.lib.euclid.Line3(\*args)
Bases: `object`


#### p()

#### v()

#### copy()

#### property p1()

#### property p2()

#### intersect(other)

#### connect(other)

### class pyacs.lib.euclid.Ray3(\*args)
Bases: `pyacs.lib.euclid.Line3`


#### p()

#### v()

### class pyacs.lib.euclid.LineSegment3(\*args)
Bases: `pyacs.lib.euclid.Line3`


#### magnitude_squared()

#### property length()

#### p()

#### v()

### class pyacs.lib.euclid.Sphere(center, radius)
Bases: `object`


#### c()

#### r()

#### copy()

#### intersect(other)

#### connect(other)

### class pyacs.lib.euclid.Plane(\*args)
Bases: `object`


#### n()

#### k()

#### copy()

#### intersect(other)

#### connect(other)
