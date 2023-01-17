
JPEG compression artefact data set
----------------------------------

Markus Kuhn -- 2019-12-11

I took three 3024 x 4032 raw photographs (camera: Google Pixel 3), and
converted the resulting *.dng files into six *.ppm files, using the
ufraw software (using six different brightness adjustments, exporting
each photo once in colour and once as a grayscale image.)

I then passed each photo through one of the following five processing
pipelines:

  pnmtopng
  cjpeg -grayscale -quality $Q1 | djpeg | pnmtopng >$@
  cjpeg -grayscale -quality $Q2 | djpeg | cjpeg -grayscale -quality $Q3 | djpeg | pnmtopng
  cjpeg -quality $Q4 | djpeg | pnmtopng
  cjpeg -quality $Q5 | djpeg | cjpeg -quality $Q6 | djpeg | pnmtopng

In other words, the image data in each of the files

  test1.png
  test1c.png
  test2.png
  test2c.png
  test3.png
  test3c.png

has gone either zero, one or two times through a JPEG
compression/decompression step.

How often did each image go through a JPEG codec?
