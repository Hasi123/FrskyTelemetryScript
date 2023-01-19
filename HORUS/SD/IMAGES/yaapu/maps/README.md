# Download offline maps using QGIS

QGIS is a very powerful and fully open source GIS (Geographic Information System) application for all platforms. It is used for surveying, scientific investigations, resource management, development planning and much more.

In the following I will show you how to use it to export basically any online map service in a format, that this widget can use. If you need larger maps, this method is much faster than GMAPCacher or downloading through MissionPlanner.

### Installation

[You can download QGIS from it's official website.](https://www.qgis.org/en/site/forusers/download.html#)
I recommend getting the LTS version, but it really shouldn't matter.

Next we are going to install a useful plugin, which lets us easily search for and open typical online web map services (like Google Maps, OpenStreetMaps, Bing Maps, etc.). Open the *Plugins* tab and click on *Manage and Install Plugins...*.
Search for QuickMapServices and install it.

### Usage

First create a new project in QGIS.

Open your preferred map sevice from the QuickMapServices plugin. You can search for it by clicking the following icon in the toolbar:
![QMS](https://user-images.githubusercontent.com/13320790/213553889-a3bc1d6c-d4eb-4a9c-aaec-25ebc936bed3.png)

Now we need to set the project coordinate reference system (CRS) to WGS84 [EPSG:4326]. Click this icon in the bottom right corner:
![CRS](https://user-images.githubusercontent.com/13320790/213545692-b2271614-a213-4c5a-820b-467d5aa8c17c.png)

Now go to the region you want to download.

Open the *Processing Toolbox* and search for the *Generate XYZ tiles (Directory)* tool.
![Processing toolbox](https://user-images.githubusercontent.com/13320790/213546267-daad1950-ba8b-4120-82f2-a034ab35817a.png)

You will have to provide the extent. For this click on the ... button either choose *Use Map Canvas Extent* to download everything thats on screen or *Draw on Canvas* to do exacty that. Input the minimum and maximum zoom levels you need (I recommend 18-20). There is no point in having zoom levels higher than 20, since the maps are not that high resolution and dowloading would take a long time. Change the *Tile Format* to JPG and the *Tile width* and *Tile height* to 100. Provide an output directory (create a new one) and optionally save the *Output html* to view the area you downloaded in a browser (you don't need this for the script). Finally click *Run* to generate the tiles.
![Generate Tiles](https://user-images.githubusercontent.com/13320790/213547363-5161570b-832e-4341-bf04-13e962749e01.png)

Copy the zoom level folders to SD/IMAGES/yaapu/maps/qgis_default/ so the directory structure looks like this:
- `/IMAGES/yaapu/maps/qgis_default/18/*`
- `/IMAGES/yaapu/maps/qgis_default/19/*`
- `/IMAGES/yaapu/maps/qgis_default/20/*`

Select QGIS as the map provider on the script configuration menu and provide your zoom levels.
![Script config](https://discuss.ardupilot.org/uploads/default/original/3X/6/6/667a761d104be5102d5a79e767ef4f50059d73c3.png)

### Please make sure you have a valid GPS sensor in OpenTX telemetry page, if not please do a sensor discovery.

## For advanced users

You can download multiple regions at once (leave it overnight for larger downloads) if you run the *Generate XYZ tiles (Directory)* tool as a batch process. Just provide the different extents you need and make sure to have all other settings the same (including the output directory).

Instead of online map services you can also provide your own georeferenced map (e.g. a geotiff) and you can even use overlapping layers to eg. draw no fly zones on the map.
