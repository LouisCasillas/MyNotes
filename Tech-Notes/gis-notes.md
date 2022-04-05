 GIS principals like projections, geoprocessing workflows, working in enterprise/multiuser geodatabases, and gis data types and models
 
 https://www.youtube.com/channel/UC34uByppapyrr-gubZMd9OQ/videos
 
 ===
 These questions assume you're interviewing for an ESRI-focused organization.

​

What is the company’s (or utility, organization, etc.) attitude towards open source (or 3rd party) tools? For example would I be encouraged or discouraged from using QGIS to solve a particular problem?
What software level and extensions would be available to me?
What is the IT infrastructure here? Is in integrated with the GIS or data group, or entirely separate? Would someone in [the group I’m interviewing for] be able to set up a VM or initialize a database, or is there a formal application process? Who controls the AGOL credit usage?
What restrictions or guides are there on cartographic work products? Do you have a strict template and style guide, or are you open to alternative visualizations?
Do you have (or plan to have) a specific geodatabase schema or would I be designing one for specific needs?
What (if any) metadata standards do you apply or require?
What are the spatial data storage methods you use? Are all data kept in local GDBs or FCs in SDE? Or can/do you store data in native enterprise database tables?
How do you manage GIS-specific professional development? Would I be encouraged/required to take formal online courses? Would I be encouraged to keep up with the industry independently via reading blogs/YouTube videos, social media, etc?
Do you encourage your employees to be active in local GIS organizations or professional societies? What value do you want to gain from them?
Have you heard about [cool new spatial technology]? Would you be open to integrating it? [this is my favorite…I love it when applicants show that they can help us grow right at the interview stage]
===

Some of the most common concepts new GIS users struggle with:

Understanding spatial coordinate reference systems (aka “crs”). Coordinate systems have numeric EPSG codes which are linked to the math involved in referencing data to (often approximate) representations of the earth as a 3D object and (sometimes) projecting that data to display 3D data in 2D. It is crucial that you know what coordinate system each dataset uses and that you are working in a common coordinate system when you are performing an operation on multiple data sets. This also matters for displaying spatial data, but some programs (eg ArcGIS) project data “on-the-fly” so a lot of people do not understand coordinate systems because the industry standard software automates dealing with them.

Understanding “geographic” vs “projected” coordinate systems - this is a naming convention from ArcGIS: one thing to note is that a geographic crs uses degrees as units and a projected crs often uses meters or feet as units.

Understanding latitude and longitude (make sure not to mix these up!- it’s a very common mistake to swap them and end up with incorrect data or results)

Understanding scale (eg how is a 1:1000 map different from a 1:100000 map)

Understanding the different file formats. Common ones are shapefiles, KML, geodatabases, and TIFF files. Some are proprietary and require certain software to read/write. You can google “GIS data formats” to learn more.

Vector vs raster data: different software/packages may refer to subcomponents of a spatial dataset differently, but vector data generally contains points, lines and polygons, whereas raster data is made up of pixels and has a defined resolution (eg 20 m x 20 m pixels).

More advanced concepts: - There is a lot behind geoprocessing operations (these are just mathematical operations applied to spatial data, eg finding the union or difference of two things) that may not be immediately clear. A common issue is when you combine two datasets, and fail to account for overlapping data so you end up double-counting.

Queries- because you come from a computer science background you should have little issue with this as usually it is just SQL or something similar.

Visualizing data- lots of people have issues with this using the standard GUIs with symbologies but for a purely python based approach it will all be in the docs for each package

Spatial statistics: there is a whole field devoted to understanding spatial data from a statistical lens, with many lengthy texts delving into the math behind more advanced concepts like kriging, density estimation or spatial autocorrelation. Animal movement analysis would fall into this category, but I don’t know off my head specifically what is recommended for human movement analysis. Unless you are just talking about data visualization, you are probably best off finding someone with expertise specific to that discipline of spatial statistics to help you or doing a literature review (eg use google scholar) to find a defensible method you can use. As with most similar things, the hard part is usually obtaining and preparing the data, knowing what kind of analysis to run and what assumptions are valid, and knowing how to interpret and validate the results.

===