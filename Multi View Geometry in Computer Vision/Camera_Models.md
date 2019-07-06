# Camera Models

* Camera is a mapping btw 3D world and 2D image.
* Camera models are matrices with particular propeties which represent camera mapping.
* The principle camera of interest is projective camera.
* The geometric entities of the camera can be computed using the matrix representation (projection center, image plane)
* Two types of specialized models : 1. finite center 2. Center at infinity.

---

## Finite Cameras

### Pinhole model

* Most specialized and simplest camera model
* Considers the central projection of points in space onto a plane.
* Center of projection is considered as origin of Euclidean coordinate system and coordinate plane Z = f as image plane or focal plane.
* All the points in plane are mapped to points on the plane as the intersection of a line passing through the point in the space and the center of projection.
* The center of projection is called camera center or optical center.
* Line perpendicular to image plane and passing through camera center is called principal axis and the point where it meets image plane is called principal point.
* Principal plane is the plane parallel to image plane and passing through center of camera.
* The camera matrix is the matrix which on multiplication with a point in space represented in its **homogenous coordinate** form gives the homogenous coordinate of projection on image plane.
  * homogenous camera projection matrix

**principal point offset** :

* we add two constants to the actual values which account for shift of origin as in general origin of coordinates in image plane may not be at principal point.
  * camera calibration matrix
  * camera as center and principal axis along z-axis, coordinate system is called camera coordinate frame.

**Camera rotation and translation** :
* 