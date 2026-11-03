****Animation Explanation Samuel Chesney****

**Importing objects to unreal**

*Step 1-*
I started to export the barstool, I export it as an FBX file:

![alt text](ImagesForREADME/FBXAttemptedExport.png)

with these settings:

![alt text](ImagesForREADME/FBXExportSettings.png)

I then moved onto setting up my project in unreal. I was using the latest version of unreal and chose to use the cinematic template:

![alt text](ImagesForREADME/UnrealProjectSetup.png)

I then dragged my FBX export of the barstool into unreal to notice something strange.

![alt text](ImagesForREADME/FBXContentDrawer.png)

The materials I had created were not being exported correctly:

![alt text](ImagesForREADME/FBXBarStoolFailedImport.png)

From researching the causes of this I found that it could be because my materials and textures were being procedurally generated in blender and this was breaking the export.

*Step 2-*
I tried to fix this by unwrapping the uv of the barstool and baking attributes of materials into pngs to use an image texture instead of the procedural nodes:

![alt text](ImagesForREADME/BarStoolUnwrappedUV.png)

![alt text](ImagesForREADME/LeatherBaseColourBake.png)

![alt text](ImagesForREADME/LeatherBaseColourOutput.png)

I then tried to export the barstool as a glTF file as my research told me that could work better:

![alt text](ImagesForREADME/BarStoolglTFExprot.png)

after trying to import this into unreal it still did not work.
I did more research and found that an earlier version of unreal (5.2.8) had a plugin developed by epic for the purpose of importing glTF files. I reversted back to this version and got this plugin to try.

![alt text](ImagesForREADME/glTFImporterPlugin.png)

I then tried to import my bar stool again and was given this popup:

![alt text](ImagesForREADME/glTFImporterPopUp.png)

When I clicked import this still did not work:

![alt text](ImagesForREADME/FailedBarStoolglTFImport.png)

I put the glTF file into a standalone glTF viewer and the output was the same which confirmed to me that it was an issue with the export rather than the import.

*Step 3-*
We need to bake every element of the materials into the materials to stop any procedural generation problems.
Lets start with the leather material.
We will start with the base colour. This holds the colour and the pattern of the leather section of the barstool:

![alt text](ImagesForREADME/LeatherBaseColourBakeSetup.png)

The pattern is very fine so we set the image to 4096x4096 pixels so as to not lose any information.
Then we switch the render engine to cycles to allow us the option to bake this, for base colour we want to set the bake type to Diffuse and make the only contribution Color.

![alt text](ImagesForREADME/LeatherBaseColourBakeSettings.png)

This bake gives us this image:
![alt text](ImagesForREADME/LeatherBaseColourBakeOutput.png)

We also need to do this for the normals of the leather texture:
![alt text](ImagesForREADME/LeatherNormalSetup.png)
![alt text](ImagesForREADME/LeatherNormalImageTexture.png)
![alt text](ImagesForREADME/LeatherNormalBakeSettings.png)
![alt text](ImagesForREADME/LeatherNormalOutput.png)

That is all that we need to bake for the leather so we now swap the procedural nodes for the new image textures we have just created:
![alt text](ImagesForREADME/NewLeatherMaterial.png)

Now we need to repeat this for metal.
The metal material has some different elemets that we need to bake. The base colour is just the colour of the metal so we do not need to bake that, lets start with roughness:
![alt text](ImagesForREADME/MetalRoughnessSetup.png)
![alt text](ImagesForREADME/MetalRoughnessBakeSettings.png)
![alt text](ImagesForREADME/MetalRoughnessOutput.png)

Now we will bake the normals for the metal:
![alt text](ImagesForREADME/MetalNormalsSetup.png)
![alt text](ImagesForREADME/MetalNormalsBakeSettings.png)
![alt text](ImagesForREADME/MetalNormalsOutput.png)

For the metallic bake we need to switch some wires in the original material to correctly bake the emission quality of the material

![alt text](ImagesForREADME/MetalEmissionRewiring.png)

![alt text](ImagesForREADME/MetalMetallicSetup.png)

![alt text](ImagesForREADME/MetalMetallicImageTexture.png)

![alt text](ImagesForREADME/MetalMetallicBakeSettings.png)

![alt text](ImagesForREADME/MetalMetallicOutput.png)

Now we need to switch the procedural nodes for these new nodes again:
![alt text](ImagesForREADME/BarStoolNewMetalTexture.png)

Now that we no longer have any procedural materials we can try to export again, we will again try to export as a glTF file:

![alt text](ImagesForREADME/BarStoolExportglTFSettings.png)

Then we will try to import this into unreal:

![alt text](ImagesForREADME/BarStoolImportSettings.png)

IT WORKED!
![alt text](ImagesForREADME/BarStoolSuccesfullyImported.png)

The leather has a clear coat but that is a simple fix, for some reason unreal gave the leather material a clear coat factor of 1 so we just drop that to 0 to remove the shine from the leather.

![alt text](ImagesForREADME/BarStoolClearCoatFix.png)

*Step 4-*
Now we will repeat this process for the cigarettes and the ashtray.
![alt text](ImagesForREADME/CigBaseColourSetup.png)
![alt text](ImagesForREADME/CigBaseColourImageTexture.png)

we copy these two nodes to every material built into the cigarettes, luckily we can bake into each node on each material at the same time instead of having to go one by one through each of the 6 materials.

![alt text](ImagesForREADME/CigBaseColourBakeSettings.png)

![alt text](ImagesForREADME/CigBaseColourOutput.png)

![alt text](ImagesForREADME/CigNormalBakeSettings.png)

![alt text](ImagesForREADME/CigNormalOutput.png)

Now we swap the procedural textures for the image textures on every material:

![alt text](ImagesForREADME/CigNewTexture.png)

Now we will export as a glTF:

![alt text](ImagesForREADME/CigExportSettings.png)

and import into unreal:

![alt text](ImagesForREADME/CigImportSettings.png)

This one worked great!

![alt text](ImagesForREADME/CigsSuccesfullyImported.png)

*Step 5-*
Importing the Jigger was the same process as the metal texture in the bar stool.

![alt text](ImagesForREADME/JiggerSuccesfulImport.png)

**Animating** 

*Step 6-*
Now that we have our objects we can start to animate.

I wanted to create a scene where the camera pans around each of the objects showing off the models and the textures. Then, as the camera passes the barstool it knocks it and the barstool falls, hitting a cigarette, and sending the cigarette flying in slow motion and landing in the jigger.

I used keyframes to model where I wanted the camera to move, adjusting the aperature, focal length, and manual focus as required to keep objects looking sharp through the camera.

![alt text](ImagesForREADME/UnrealOutputSequencerV1.png)

I then keyframed the barstool falling over and knocking the cigarette flying.

To export this first version I had to download an application called ffmpeg which I used for the CLI encoder built into Unreal:

![alt text](ImagesForREADME/UnrealEncoderSettings.png)

I then exported the first version of the animation sequence.

The first version of the sequence was a good baseline and showed me what I wanted the animation to roughly look like and allowed me to get more comfortable with the tool. However, the cigarette's flight did not look and I wanted the camera to slow down as it pans over each object.

*Step 7-*
Adjusting the camera pan speed was easy enough and achieved by seperating the keyframes when the camera was closer to the objects to be further apart and give the viewer more time to take in the object.
To make the cigarette flight look more natural I decided that the rate at which it rotated needed to be increased. I decided it would do a full rotation every 30 frames (1 second) and half a rotation every 15 frames. I went through the entire sequence amending this ration rate.

This made the rate of rotation look much better for version 2 of the output but there was still something not quite right about it so I will need to fix that in version 3.

![alt text](ImagesForREADME/UnrealOutputSequencerV2.png)

To get version two of the unreal output to github I had to export it with quality high instead of epic so that it was under the 100MB restriction of github.

*Step 7-*
To make the cigarette flight look more natural I decided to change the flight path to be steeper which did make it look more natural, I also did not like how askey the rotation was, I found this menu:

![alt text](ImagesForREADME/RotationCurves.png)

Which enabled me to flatten the curves for pitch and yaw to make the rotation look more like it was on one axis, I squished these curves and that make the flight rotation something I was more happy with.

There was also an issue with the cigarette clipping into the cushion of the stool so I adjusted the flight path to prevent this.

I also edited the skybox to give the scene a more evening-like glow:
![alt text](ImagesForREADME/LightEditing.png)

![alt text](ImagesForREADME/EveningLightResult.png)

I also changed the material of the plane the scene was sitting on to a material included in the unreal engine which looked like wood to give the feeling of an oldschool hardwood floored pub:

![alt text](ImagesForREADME/NewFloor.png)

I also added walls to the room to break the floating in space scene.

![alt text](ImagesForREADME/RoomWithWalls.png)