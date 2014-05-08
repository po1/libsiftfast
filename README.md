libsiftfast: author zerofrog(@gmail.com)
----------------------------------------
Ported to catkin by Paul Mathieu (paul.mathieu@pal-robotics.com)

This package contains `libsiftfast.so`, a really fast SIFT implementation using
SSE and OpenMP (also fixes some bugs from lowe's code, so outputs are similar,
but not exact). The usage is very similar to David Lowe's sift program.


SIFT is based on David G. Lowe, "Distinctive image features from
scale-invariant keypoints, "International Journal of Computer Vision, 60, 2
(2004), pp. 91-110.


Comparisons with other SIFT Code
--------------------------------

The default setting of siftfast produce the same output as Lowe's free sift
program. On a quad-core Core2Duo machine with OpenMP, siftfast goes about 6x
faster than lowe's sift program for 640x480 images.
