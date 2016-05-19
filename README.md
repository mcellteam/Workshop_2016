# Workshop_2016
## Repository for models, descriptions, and code to be used for the 2016 Workshop.

Ideally we would like the 2016 workshop to demonstrate a pipelining of our tools using a single multi-scale model. However, since many of our tools operate on different scales, it may be necessary to simplify certain aspects of the model or otherwise address the multi-scale issue so it will be manageable within the time and computational constraints of the workshop.

This repository has been created as a place to work out an appropriate model for the workshop consistent with our February 25th decision.

At this point, the candidate tools for such a joint model are:

* **CellBlender**
* **MCell**
* **BioNetGen**
* **CellOrganizer**

Please feel free to add/delete tools that might participate in this portion of the workshop.

As of March 31st, we have a preliminary model from CellOrganizer with an organelle added by CellBlender:

![Cell1 in CellBlender/MCell](Cell1_Test1.gif?raw=true "Cell1 in CellBlender/MCell")

## CellOrganizer

The CellOrganizer project provides tools for

* learning generative models of cell organization directly from images
* storing and retrieving those models
* synthesizing cell images (or other representations) from one or more models

In this section of the tutorial we are going to use CellOrganizer to

* train a framework model from simple 3D shapes
* synthesize a framwork instance from the model and export it as a Wavefront .obj file

### Training a model with simple geometries

`img2slml` is the main function used for training. It takes five inputs

* a flag describing the dimensionality of the data
* images for the nuclear channel
* images for the cell shape channel
* images for the protein channel (optional)
* options used to change default model settings.

### Image synthesis using a model trained on simple geometries

The main function for image synthesis is `slml2img`. This function takes two inputs
* a cell array of paths to the models from which we want to synthesize
* options used to change default synthesis settings.
