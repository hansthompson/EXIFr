# EXIFr : Natively read EXIF tags from R

[![DOI](https://zenodo.org/badge/19481/cmartin/EXIFr.svg)](https://zenodo.org/badge/latestdoi/19481/cmartin/EXIFr) [![Build Status](https://travis-ci.org/cmartin/EXIFr.svg)](https://travis-ci.org/cmartin/EXIFr) [![Coverage Status](https://coveralls.io/repos/cmartin/EXIFr/badge.svg?branch=master&service=github)](https://coveralls.io/github/cmartin/EXIFr?branch=master)

This package natively reads EXIF tags from digital images. It does not rely on any external libraries or binary executables.

To keep things as simple as possible for the beginning, only the following tags are currently available :

* ExposureTime
* ApertureValue
* FocalLength
* ISOSpeedRatings
* PixelYDimension
* PixelXDimension
* DateTime
* Make
* Model

All values are returned as provided in the image file, so for example ExposureTime is **"1/3200"** and not **0.0003125**

N.B. A utility function is provided to convert from the rational format `rational_to_numeric("1/3200")`

## To install : 

```r
library(devtools)
devtools::install_github("cmartin/EXIFr")
```

## To try the code with one of the example images : 

```r
library(EXIFr)

# To list all tags : 
image_path = system.file("extdata", "preview.jpg", package = "EXIFr")
read_exif_tags(image_path)
```

```
Make            : Canon 
Model           : Canon EOS DIGITAL REBEL XS 
DateTime        : 2013:07:09 10:23:47 
ExposureTime    : 1/3200 
ISOSpeedRatings : 800 
ApertureValue   : 43/8 
FocalLength     : 18/1 
PixelXDimension : 100 
PixelYDimension : 67 
```

```r
# To view the value of a specific tag
read_exif_tags(image_path)[["ApertureValue"]]
```

```
[1] "43/8"
```

```r
# or
rational_to_numeric(read_exif_tags(image_path)[["ApertureValue"]])
```

```
[1] 5.375
```

## If you need help with the EXIF format
The following resources were particularly useful :

* http://www.cipa.jp/std/documents/e/DC-008-2012_E.pdf
* http://code.flickr.net/2012/06/01/parsing-exif-client-side-using-javascript-2/
* http://www.media.mit.edu/pia/Research/deepview/exif.html

## Problems : 
Please report any bugs to the [GitHub issue tracker](https://github.com/cmartin/EXIFr/issues) and write any questions to <charles.martin1@uqtr.ca>

## Citation
If this code is useful to you, please cite as : 


```
Charles A. Martin (2015). EXIFr: Natively read EXIF tags from R. https://github.com/cmartin/EXIFr. DOI:10.5281/zenodo.34691. 
```
