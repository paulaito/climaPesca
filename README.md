<h1>Contribution for ClimaPesca project</h1>

This was my final graduation project, whose title was "Time-series environmental database for Portuguese coastal areas and mapping the
vulnerability of marine biological resources to climate change: a GIS-approach", and it was a collaboration for the <a title="" href="http://climapesca.com/">ClimaPesca</a> project. My main goals were:

<ul>
<li> Creating a time-series environmental database for Portuguese coastal areas;
<li> Creating and exporting thousands maps as tif files.</p>
</ul>
<p>
In the following sections, the methodology will be furtherly explained.</p>

<h2>Time-series database with environmental data</h2>
A time-series database with monthly data from 1985 until 2020 for the three Portuguese coastal areas (North, Centre and South) was created. 
</ul>
<p><h3>Data extraction</p></h3>
Part of the data was extracted from Copernicus and NASA products, while other datasets had to be acquired from THREDDS catalog via Python coding, which is available <a href="https://github.com/paulaito/climapesca/tree/main/scripts/download_data">here</a>.
<p>
<p><h3>Data transformation (converting raster into tabular data)</p></h3>
Once all rasters were obtained, it was necessary to extract the monthly average on each the coastal area from the raster datasets, i.e. transforming raster data into tabular data. Almost all data was transformed with R programming <a href="https://github.com/paulaito/climapesca/tree/main/scripts/download_data">(code available here)</a> using <i>raster</i>, <i>netcdf</i> and <i>stringr</i> packages, except wind data from NASA CCMP, which had to be converted into tabular data through Python programming <a href="https://github.com/paulaito/climapesca/tree/main/scripts/environdata/ccmp_wind">(code available here)</a>. The Python packages used in this process were <i>arcpy</i>, <i>pandas</i>, <i>openpyxl</i>, <i>re</i> and <i>os</i>.
<p>
<p><h3>Data structure (organizing into a database)</p></h3>
The output from the previous step was csv files containing monthly averages for the three coastal areas for each year and each variable. Now, all data were structured in one single database (xlsx file). This procedure was automized using <i>pandas</i> and <i>os</i> and the code is found <a href="https://github.com/paulaito/climapesca/tree/main/scripts/environdata/database">here</a>.
<p><p>
<h2>Maps creation and export</h2>
Habitat suitabily, marginality and specialization raster datasets for ca. 60 species occuring in the coast of Portugal were provided. From these datasets, the overall procedure for creating and exporting map images were:
<p><ul>
<p><strong><li>Data conversion (converting Ascii into NetCDF) files</strong>
<p>All maps were provided in Ascii format, which were converted into NetCDF files using arcpy functions <a href=https://github.com/paulaito/climapesca/tree/main/scripts/convert_asc_to_nc>(code here)</a>.
<p><li><strong>Creating customized layout template and symbologies</p></strong>
<p>The layout templates (.qpt) and symbologies (.qml) were created inside QGIS.
<p><strong><li>Creating and exporting map images</strong></p>
<p>This step was entired automized using qgis.core (<i>PyQGIS</i>)functions, classes and objects, and the code is available <a href=https://github.com/paulaito/climapesca/tree/main/scripts/layout_mapImages>here</a>. Two programs were written: one for habitat suitability maps, and another for marginality and specialization maps, and this was done due to different properties that each of these data have.
