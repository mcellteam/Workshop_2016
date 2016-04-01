# Workshop_2016
## Repository for models, descriptions, and code to be used for the 2016 Workshop.

Ideally we would like the 2016 workshop to demonstrate a pipelining of our tools using a single multi-scale model. However, since many of our tools operate on different scales, it may be necessary to simplify certain aspects of the model or otherwise address the multi-scale issue so it will be manageable within the time and computational constraints of the workshop.

This repository has been created as a place to work out an appropriate model for the workshop consistent with our February 25th decision.

At this point, the candidate tools for such a joint model are:

* **CellBlender**
* **MCell**
* **BioNetGen**
* **Cell Organizer**

Please feel free to add/delete tools that might participate in this portion of the workshop.

At this time we are working toward the "Organelle" model that looks like this:

![Organelle Model](organelle_mcell.gif?raw=true "Organelle Model")

If we start with Cell Organizer, we might try to build the "Organelle" model geometry using a series of slices something like this:

![Organelle Slices](organelle_fill.gif?raw=true "Organelle Slices")

The output from CellOrganizer would ideally be a model mesh that the students can simulate in CellBlender/MCell:

![Organelle Wire Frame](organelle_wire.png?raw=true "Organelle Wire Frame")

As of March 31st, we have a preliminary model from CellOrganizer with an organelle added by CellBlender:

![Cell1 in CellBlender/MCell](Cell1_Test1.gif?raw=true "Cell1 in CellBlender/MCell")
