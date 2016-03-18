# Making MSFF Prism Maps

**Eric M. Huntley, MUP**  
New Mappings Collaboratory, University of Kentucky  
Political Space Economy Lab, Virginia Tech  

![final image](https://raw.githubusercontent.com/designedspace/MSFF_Docs/master/Files/Media/0_FinalImage.PNG "Final image")  

This procedure will produce [prism maps](http://blog.thematicmapping.org/2008/05/prism-maps-in-google-earth-and-uuorld.html) (also called 3D Choropleth maps) according to the style developed by the author for the Political Space Economy Lab's "Moonlights, Sunspots, and Frontier Finance" exhibit in Fall 2013. A prism map is a thematic map in which "each enumeration unit area as the base of a prism whose height is proportional to the intensity value of the mapped phenomenon" (Jenks and Caspall 1971, 219). These are seen by some cartographers as the most effective way of visualizing numerical data in a choropleth map (Slocum et al. 2004).

The following software packages are required:  
  * ESRI ArcScene 10.1  
    * *N.B., releases after 10.1 contain a still-unsolved bug (known as Bug #000085475) that prevents some users (including this one) from exporting scenes in the VRML file format. I spent two afternoons searching for a workaround, but ultimately had to downgrade my Arc installation*.
  * Rhinoceros  
  * VRay  
  * Photoshop  

## 1. Symbolize and Extrude Map in ArcScene  

#### 1.1 Import Shapefiles  

1. Add a connection to your project folder using the ArcScene catalog window. 
![arcscene](https://raw.githubusercontent.com/designedspace/MSFF_Docs/master/Files/Media/1_1_arcscene.PNG "ArcScene")  
2. Add the shapefile that contains the data of interest (in this example, 2004 HMDA data aggregated to Census Tracts in Michigan), as well as any additional features that might prove cartographically useful (in this example, the Detroit municipal boundary, and the land areas of Ontario, Ohio, and Indiana).
3. Check the scene's coordinate system; if the scene is not projected appropriately, select an appropriate projection. In this example, I used NAD_1927_Michigan_GeoRef_Feet_US.

#### 1.2 Symbolize and Extrude Enumeration Units   

![symbology](https://raw.githubusercontent.com/designedspace/MSFF_Docs/master/Files/Media/1_2_symbology.PNG "Symbology")  
1. Open the properties window for the layer of interest and navigate to the Symbology tab. Symbolize the variable of interest using a graduated color scheme with a white-to-grey gradient. Limit the number of classes to 4 or 5 and choose an appropriate classification method. Make sure that the gradient is such that higher values receive darker colors - while this appears to be the opposite of the desired result, the image will be inverted later in Photoshop, which imbues the prisms with the eerie glowing-from-the-base character. The white-to-grey gradient is chosen over a white-to-black for similar reasons.  
    * N.B., if you are producing a series of maps that are meant to be comparable, all maps should use the same classification scheme and this classification scheme should be based on the year with the largest range of values.    
![extrusion](https://raw.githubusercontent.com/designedspace/MSFF_Docs/master/Files/Media/1_2_extrusion.PNG "Extrusion")  
2. Navigate to the Extrusion tab and check "Extrude Features in Layer." Select the same variable as above. Note that, depending on the variable's range, it may be necessary to scale the value (as shown).  

#### 1.3 Export as VRML (.wrl)  
![export](https://raw.githubusercontent.com/designedspace/MSFF_Docs/master/Files/Media/1_3_export.PNG "Export at VRML")  
1. Export the scene as a VRML (.wrl) file (File > Export > 3D). As mentioned above, a persistent bug in versions of ArcScene later than 10.1 might cause the program to crash, preventing a 3D export. If this is the case, it will be necessary to downgrade ArcScene.  

## 2. Render in Rhinoceros  

#### 2.1 Import VRML file  

1. Create a new Rhino project using the "Large Objects - Feet.3dm" template.  
![rotate](https://raw.githubusercontent.com/designedspace/MSFF_Docs/master/Files/Media/2_1_rotate.gif "Rotate model")  
2. Import the VRML file exported from ArcScene. The first thing you'll notice is that the model is rotated in such a way that its ground plane is along Rhino's z-axis. To fix this, ensure that the Right viewport is active, select all objects, type "rotate", type "0", hold shift and click at an angle orthoganal to the model, and type "90" to rotate the model 90 degrees. The model's ground plane should now coincide with Rhino's x-y plane.  
3. Delete the directional light that was imported along with the model.  
4. Relocate any supplementary geometry (boundaries, lakes, etc.) to a different layer.  

#### 2.2 Set camera  

1. Change the perspective viewport's properties such that it uses parallel projection instead of perspective.  
2. In the top viewport, create a new line of arbitrary length at a 0 degree angle whose start is the project's origin (this will be used to set the camera and its target). In the front viewport, rotate it up from the ground plane by 30 degrees. In the top viewport, rotate it so that it makes an angle appropriate for the area under consideration. Pictured below is the the result of this process in the case of Detroit.  
![set camera](https://raw.githubusercontent.com/designedspace/MSFF_Docs/master/Files/Media/2_2_camera.PNG "Set camera")  
3. Make sure the perspective viewport is active. Navigate to "Place Camera and Target" (View > Set Camera). Place the camera at the elevated end of the line, and place the target at the end of the line in contact with the ground plane. Now adjust the zoom settings until the frame is positioned as desired. Pictured below is (again) the result of this process in the case of Detroit.  
![camera placement](https://raw.githubusercontent.com/designedspace/MSFF_Docs/master/Files/Media/2_2_cameraplacement.PNG "Camera Placement")  
4. Save the view using the "NamedView" command.  

#### 2.3 Light and Render  
1. Create a large rectangular light on a new layer using the "RectangularLight" command. Size it so that is larger than the area of interest. Move it vertically by 3,750,000 ft - it's important to keep this consistent, as the intensity of the light varies with distance.  
2. The desired format for these images is 10"x10", printed at 300 dpi; therefore, change the VRay output size to 3000x3000 and ensure that "override viewport" is checked. Also check that the "05_VeryHigh_Quality_Exterior" preset is selected.  Hide all layers except the light and the data of interest.  
![rendered](https://raw.githubusercontent.com/designedspace/MSFF_Docs/master/Files/Media/2_3_render.PNG "Rendered")  
3. Render! The output should look something like the above image. Save it as a PNG file to maintain background transparency.  
4. Hide the layer of interest and display additional layers (in this example, the Detroit municipal boundary and surrounding land areas). Render them one by one, again making sure to save them as PNGs to preserve transparency.  

## 3. Retouch in Photoshop  

In all that follows, the color - white or magenta - should be decided on a case-by-case basis.

* **MSFF Magenta** (C=1, M=98, Y=0, K=0) should be used where a 'negative' variable is under consideration (e.g., mortgage denials).  
* **White** (C=0,M=0,Y=0,K=0) should be used where a a 'positive' variable is under consideration (e.g., amount of mortgage capital).

#### 3.1 Add, Invert, and Color Rendered Data  
1. Open the rendered prism map, invert it (ctrl-i), and change the file to CMYK color space. **It's crucial that you invert before converting to CMYK!** Add a new background layer and fill it with true black (C=100, M=100, Y=100, K=100).  
![levels](https://raw.githubusercontent.com/designedspace/MSFF_Docs/master/Files/Media/3_1_1levels.PNG "Levels")  
2. Using the levels tool, pull up the shadows (left-most triangle) so that it sits below the first peak - you don't want to lose all detail in the darkest greys. A value of 20 worked well for me.
3. Add a new layer fill it with the MSFF magenta (C=1, M=98, Y=0, K=0) and switch its blend mode to overlay. This should always occupy the top position in the layer draw order. (*Skip this step if making a 'white' map*).  
4. Using the layer's blending options, create a stroke with a width of 3 pixels using the map color around the rendered data. 
5. Add 45 degree diagonal hatch below the data layer. See the resources folder in this repo for the one I used in both Illustrator and PNG format. The resulting image should look like the one below.  
![resulting image](https://raw.githubusercontent.com/designedspace/MSFF_Docs/master/Files/Media/3_1_2resulting.PNG "Resulting Image")  

#### 3.2 Add Additional Elements  

This last collection of steps must be tailored to the needs of a particular map. As such, the following should only be taken as guidance.  

1. Add any additional geometry you rendered out of Rhino. In this example case, I added the land area that surrounds Michigan, including Ontario, Indiana, and Ohio (data sourced from the US and Canadian Census respectively), as well as the Detroit municipal boundary (in a separate render).  
![other land area](https://raw.githubusercontent.com/designedspace/MSFF_Docs/master/Files/Media/3_2_1canadaohio.PNG "Other Land")  
2. Using the land area's blending options, I applied a true black (C=100, M=100, Y=100, K=100) color overlay and a stroke in MSFF magenta of width 3 px. As a result, Lake St. Clair and Lake Erie are filled with a hatch and the surrounding land areas are simply outlined in the map color.  
![detroit offset](https://raw.githubusercontent.com/designedspace/MSFF_Docs/master/Files/Media/3_2_2detroit.PNG "Detroit")  
3. I then added Detroit's muncipal boundary, added a white color overlay and a magenta stroke using its blending options (this would be a magenta overlay and a white stroke in the case of a white map). I set the opacity of this layer to 40%. I then duplicated this layer, changed its overlay to MSFF magenta, removed the stroke, made it fully opaque, and vertically offset it. Finally, I added some leading lines to help guide the reader's eye.
4. The final map appears below.  
![final image](https://raw.githubusercontent.com/designedspace/MSFF_Docs/master/Files/Media/0_FinalImage.PNG "Final image") 

## References
Jenks, George F. and Fred C. Caspall. 1971. "Error on Choroplethic Maps: Definition, Measurement, Reduction." *Annals of the Association of American Geographers* 61 (2): 217-244.

Slocum, Terry A., Robert B. McMaster, Fritz C. Kessler, and Hugh H. Howard. 2004. *Thematic Cartography and Geographic Visualization*. 2nd ed. Upper Saddle River: Prentice Hall.