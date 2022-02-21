# PyImageJ: Python wrapper for ImageJ2

[![Image.sc forum](https://img.shields.io/badge/dynamic/json.svg?label=forum&url=https%3A%2F%2Fforum.image.sc%2Ftags%2Fpyimagej.json&query=%24.topic_list.tags.0.topic_count&colorB=brightgreen&suffix=%20topics&logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAA4AAAAOCAYAAAAfSC3RAAABPklEQVR42m3SyyqFURTA8Y2BER0TDyExZ+aSPIKUlPIITFzKeQWXwhBlQrmFgUzMMFLKZeguBu5y+//17dP3nc5vuPdee6299gohUYYaDGOyyACq4JmQVoFujOMR77hNfOAGM+hBOQqB9TjHD36xhAa04RCuuXeKOvwHVWIKL9jCK2bRiV284QgL8MwEjAneeo9VNOEaBhzALGtoRy02cIcWhE34jj5YxgW+E5Z4iTPkMYpPLCNY3hdOYEfNbKYdmNngZ1jyEzw7h7AIb3fRTQ95OAZ6yQpGYHMMtOTgouktYwxuXsHgWLLl+4x++Kx1FJrjLTagA77bTPvYgw1rRqY56e+w7GNYsqX6JfPwi7aR+Y5SA+BXtKIRfkfJAYgj14tpOF6+I46c4/cAM3UhM3JxyKsxiOIhH0IO6SH/A1Kb1WBeUjbkAAAAAElFTkSuQmCC)](https://forum.image.sc/tag/pyimagej)
[![Build Status](https://github.com/imagej/pyimagej/actions/workflows/python-test-conda.yml/badge.svg?branch=master)](https://github.com/imagej/pyimagej/actions/workflows/python-test-conda.yml)

PyImageJ provides a set of wrapper functions for integration between [ImageJ2]
and Python. It also supports the original [ImageJ] API and data structures.

A major advantage of this approach is the ability to combine ImageJ and ImageJ2
with other tools available from the Python software ecosystem, including NumPy,
SciPy, scikit-image, [CellProfiler], [OpenCV], [ITK] and many more.

## Quick Start

Jump into the [documentation and tutorials](doc/README.md) to get started!

## Installation

PyImageJ can be installed using conda. Here is how to create and activate
a new conda environment with PyImageJ available:

```
conda create -n pyimagej -c conda-forge pyimagej openjdk=8
conda activate pyimagej
```

Alternately, it is possible to install PyImageJ with pip.

For detailed installation instructions and requirements,
see [Install.md](doc/Install.md).

## Usage

The first step when using PyImageJ is to create an ImageJ2 gateway.
This gateway can point to any official release of ImageJ2 or to a local
installation. Using the gateway, you have full access to the ImageJ2 API,
plus utility functions for translating between Python (NumPy, xarray,
pandas, etc.) and Java (ImageJ2, ImgLib2, etc.) structures.

For instructions on how to start up the gateway for various settings,
see [Initialization.md](doc/Initialization.md).

Here is an example of opening an image using ImageJ2 and displaying it:

```python
# Create an ImageJ2 gateway with the newest available version of ImageJ2.
import imagej
ij = imagej.init()

# Load an image.
image_url = 'https://imagej.net/images/clown.jpg'
jimage = ij.io().open(image_url)

# Convert the image from ImageJ2 to xarray, a package that adds
# labeled datasets to numpy (http://xarray.pydata.org/en/stable/).
image = ij.py.from_java(jimage)

# Display the image (backed by matplotlib).
ij.py.show(image, cmap='gray')
```

For more, see the [documentation and tutorials](doc/README.md).

## Getting Help

[The Scientific Community Image Forum](https://forum.image.sc/tag/pyimagej)
is the best place to get general help on usage of PyImageJ, ImageJ2, and any
other image processing tasks. Bugs can be reported to the PyImageJ GitHub
[issue tracker](issues).

## Contributing

All contributions, reports, and ideas are welcome. Contribution is done
via pull requests onto the pyimagej repository.

Most development discussion takes place on the pyimagej
[GitHub repository](https://github.com/imagej/pyimagej).
You can also reach the developers at the
[pyimagej gitter](https://gitter.im/imagej/pyimagej).

------------------------------------------------------------------------------

[ImageJ2][https://imagej.net/software/imagej2]
[ImageJ][https://imagej.net/software/imagej]
[CellProfiler][https://imagej.net/software/cellprofiler]
[OpenCV][https://imagej.net/software/opencv]
[ITK][https://imagej.net/software/itk]
