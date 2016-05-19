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

### Generating simple geometries
CellOrganizer has a helper function that we used to generate a collection of images.
We are going to use these simple geometries to train a model.

![Cell1 in CellBlender/MCell](cellorganizer/simple_geometries_dataset.png "Simple geometries dataset snapshot")

### Training a model with simple geometries

`img2slml` is the main function used for training. It takes five inputs

* a flag describing the dimensionality of the data
* images for the nuclear channel
* images for the cell shape channel
* images for the protein channel (optional)
* options used to change default model settings.

```
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% TRAIN MODEL WITH SIMPLE GEOMETRIES
clear options

% location of TIF files and resolution
dna = './synthetic_images/*_0.tif';
cell = './synthetic_images/*_1.tif';
options.model.resolution = [0.049, 0.049, 0.2000];

%training flag is set to framework because want to train a model for
%nuclear and cell shape
options.train.flag = 'framework';

%train model at full resolution
options.downsampling = [1 1 1];

%combination of supported model class and type
options.nucleus.name = 'ellipsoids';
options.nucleus.class = 'nuclear_membrane';
options.nucleus.type = 'cylindrical_surface';

%combination of supported model class and type
options.cell.name = 'ellipsoids';
options.cell.class = 'cell_membrane';
options.cell.type = 'ratio';

%output filename
options.model.filename = 'model.mat';

%helper options
options.verbose = true;
options.debug = true;

%CellOrganizer call
img2slml( '3D', dna, cell, [], options );
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
```

### Image synthesis using a model trained on simple geometries

`slml2img` is the main function for image synthesis. This function takes two inputs
* a cell array of paths to the models from which we want to synthesize
* options used to change default synthesis settings.
