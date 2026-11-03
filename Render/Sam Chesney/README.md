****Samuel Chesney Renders****

**Cigarettes and ashtray**

*Idea:*
create a model of an ashtray and cigarettes.

*Step 1 -*
For the ashtray, I started with a circle which I extruded up to form a sort of bowl shape, for the basic cigarette model I used a cylinder.

![alt text](ImagesForReadme/AshtrayStarting.png)

This stage provided the rough idea for the project moving forward.

*Step 2-*
I started to model the ashtray some more adding indents where people could rest their cigarettes when not actively smoking. I created three of these indents around the ashtray.

![alt text](ImagesForReadme/AshtrayIndents.png)

Then I added two cigarette models to the ashtray, keeping the second one shorter to allow for a cigarette to be getting smoked.

![alt text](ImagesForReadme/AshtrayWithCigarettes.png)

*Step 3-*
I gave the ashtray a simple material and started to texture the cigarettes

![alt text](ImagesForReadme/AshtrayMaterial.png)

*Step 4-*
I identified the different parts of a cigarette: the paper, filter, butt, wrap, and tobacco. Each of these will require a different material.
This is the material for the butt:

![alt text](ImagesForReadme/ButtTexture.png)
This is the material for the paper:

![alt text](ImagesForReadme/PaperTexture.png)
This is the material for the wrap:

![alt text](ImagesForReadme/WrapTexture.png)
This is the material for the tobacco:

![alt text](ImagesForReadme/TobaccoTexture.png)

I then decided to make one of the cigarettes ends lit and created this material:

![alt text](ImagesForReadme/BurningTexture.png)
This is the material for the filter:

![alt text](ImagesForReadme/FilterTexture.png)

*step 5-*
At this stage the cigarettes and the ashtray were looking good but I wanted to add some ash to the ashtray to make it look more used.
I started by modelling 5 ash 'bits' that I can scatter on the ashtray, these are the ash bits:

![alt text](ImagesForReadme/AshBits.png)

I then tried to scatter them using geometry nodes and reached this set of nodes:

![alt text](ImagesForReadme/AshGeometry.png)

This was good and looked effective but I wanted to focus the ash in areas which more reasonable; the middle of the ashtray and under the indents and lit cigarette. Do do this I used a weight paint and plugged that into the distribution mask on the scatter on surface geometry node. This was the scatter mask that I painted:

![alt text](ImagesForReadme/AshWeight.png)

Tweaking the settings and getting the ash to the way I wanted it to be then got me to this result:

![alt text](CigarettesAndAshtray_Final_Render.png)

To create this final render I wanted to have a cleaner light set up which allowed all the details of the materials to be visible. I used two spotlights and two point lights to achieve the lighting that I wanted.

**Jigger**

*Step 1-*
The jigger was a much simpler model to create, I started with a cylinder which I then transformed to pinch in the middle with loop cuts then extend up to create the two 'cones' of the jigger. This is the model I had after finishing the modelling:

![alt text](ImagesForReadme/JiggerModel.png)

*Step 2-*
I wanted this jigger to have a sort of dirty used metal look so I started to create the metal texture:

![alt text](ImagesForReadme/JiggerMaterial.png)

This material gave the jigger this look:

![alt text](ImagesForReadme/JiggerPreview.png)

*Step 3-*
I was happy with this so I started to work on the render. I wanted to be able to show the lines in the top and the bottom of the jigger and the inside, I used 4 point lights to light up the sides, the back and the top to get to this final render:

![alt text](Jigger_Final_Render.png)

**Bar Stool**

*Step 1-*
The bar stool model was individually the most complex model. it started with a cylinder which I extruded out and added loop cuts to to give it the rough shape that I wanted. I then selected an area at a height where I thought would be reasonable to create a footrest.

![alt text](ImagesForReadme/BarStoolModel.png)

*Step 2-*
Once I had the shape of the barstool where I wanted it to be I started to move onto creating the materials. I wanted the seat to be a sort of red leather and the stand to be a brass sort of metal.
The metal material was created with the same method as the metal for the jigger material.

This was the material I made for the leather:

![alt text](ImagesForReadme/LeatherMaterial.png)

And, this was the material I made for the metal stand:

![alt text](ImagesForReadme/BarStoolMetalMaterial.png)

*Step 3-*
From this Stage I was happy so moved onto creating the render. For this render I wanted to show the sheen of the metal so used a two spot lights pointing at the front of the stool to show the shine off the metal, I also used a point light behind the stool to give it some back lighting and create softer shadows. The leather cushion is lit by the same spot light that is lighting the front right of the stool which allows for the curve of the leather to be shown by a shadow on the back of it. There is also a spotlight pointing at the left side of the barstool which allows for a the shadow on the back of the bottom of the stand and the shadow coming from the stand being projected onto the base. The point light at the back creates the nice blue tinge you see on top of the footrest.

![alt text](BarStool_Final_Render.png)
