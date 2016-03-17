# Making MSFF Prism Maps

**Eric M. Huntley, MUP**  
Political Space Economy Lab, Virginia Tech  
New Mappings Collaboratory, University of Kentucky

This procedure will produce [prism maps](http://blog.thematicmapping.org/2008/05/prism-maps-in-google-earth-and-uuorld.html) (also called 3d Choropleth maps) according to the style developed by the author for the Political Space Economy Lab's "Moonlights, Sunspots, and Frontier Finance" in Fall 2013. A prism map is a thematic map in which "each enumeration unit area as the base of a prism whose height is proportional to the intensity value of the mapped phenomenon" (Jenks and Caspall 1971, 219). These are seen by some cartographers as the most effective way of visualizing numerical data in a choropleth map (Slocum et al. 2004).

The following software packages are required:  
  * ESRI ArcScene 10.1  
    * *N.B., releases after 10.1 contain a still-unsolved bug (known as Bug #000085475) that prevents some users (including this one) from exporting scenes in the VRML file format. I spent two afternoons searching for a workaround, but ultimately had to downgrade my Arc installation*.
  * Rhinoceros  
  * VRay  
  * Adobe Photoshop

## 1. Symbolize and Extrude Map in ArcScene

#### 1.1 Import Shapefiles

1. Add a connection to your project folder using the ArcScene catalog window. 
![arcscene](https://raw.githubusercontent.com/designedspace/MSFF_Docs/master/Files/Media/1_1_arcscene.PNG "ArcScene")  
2. Add the shapefile that contains the data of interest (in this example, 2004 HMDA data aggregated to Census Tracts in Michigan), as well as any additional features of interest (e.g., bodies of water, political boundaries).  
3. Check the scene's coordinate system; if the scene is not projected appropriately, select an appropriate projection (State Plane or UTM Zone).

#### 1.2 Symbolize and Extrude Enumeration Units

![symbology](https://raw.githubusercontent.com/designedspace/MSFF_Docs/master/Files/Media/1_2_symbology.PNG "Symbology")  
1. Open the properties window for the layer of interest and navigate to the Symbology tab. Symbolize the variable of interest using a graduated color scheme with a black-to-white gradient. Select the maximum number of classes (32) and use the quantile classification method. Make sure to flip the symbols so that higher values receive brighter colors and to remove all symbol borders.
    * *N.B., if you are producing a series of maps that are meant to be comparable, all maps should use the same classification scheme and this classification scheme should be based on the year with the largest range of values.  
![extrusion](https://raw.githubusercontent.com/designedspace/MSFF_Docs/master/Files/Media/1_2_extrusion.PNG "Extrusion")  
2. Navigate to the Extrusion tab and check "Extrude Features in Layer." Select the same variable as above. Note that, depending on the variable's range, it may be necessary to scale the value (as shown).
#### 1.3 Export as VRML (.wrl)
![export](https://raw.githubusercontent.com/designedspace/MSFF_Docs/master/Files/Media/1_3_export.PNG "Export at VRML")  
1. Export the scene as a VRML (.wrl) file (File > Export > 3D). As mentioned above, a persistent bug in versions of ArcScene later than 10.1 might prevent a 3D export. If this is the case, it will be necessary to downgrade ArcScene.

## 2. Render in Rhinoceros

#### 2.1 Import VRML file
#### 2.2 Set camera
#### 2.3 Create rectangular light
#### 2.4 Modify VRay settings
#### 2.5 Render
#### 2.6 Make2D

## 3. Linework in Illustrator

#### 3.1
####
####

## 4. Retouch in Photoshop



## References
Jenks, George F. and Fred C. Caspall. 1971. "Error on Choroplethic Maps: Definition, Measurement, Reduction." *Annals of the Association of Americal Geographers* 61 (2): 217-244.

Slocum, Terry A., Robert B. McMaster, Fritz C. Kessler, and Hugh H. Howard. 2004. *Thematic Cartography and Geographic Visualization*. 2nd ed. Upper Saddle River: Prentice Hall.