<!--
.. title: Strip Geospatial Data from Image Headers
.. slug: strip-geo-images
.. date: 2018-04-12 08:16:53 UTC-05:00
.. tags: exiftool, exif, images, geodata, privacy
.. category: 
.. link: 
.. description: How to use ExifTool to remove spatial metadata from image headers.
.. type: text
-->

Reblogged from [a Mastodon post](https://social.coop/@paregorios/99796064822455556):

Given that most phone cameras and many other digital cameras automatically embed spatial data in image headers, I'd like to point out that the following command-line invocation of [Phil Harvey's ExifTool](https://www.sno.phy.queensu.ca/~phil/exiftool/) removes it when that's what you'd prefer:

```
exiftool -gps:all= -xmp:geotag= your_image.jpg
```




