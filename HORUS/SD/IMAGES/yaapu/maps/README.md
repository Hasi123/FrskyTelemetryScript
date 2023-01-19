# Download offline maps using QGIS

QGIS is a very powerful and fully open source GIS (Geographic Information System) application for all platforms. It is used for surveying, scientific investigations, resource management, development planning and much more.

In the following I will show you how to use it to export basically any online map service in a format, that this widget can use. If you need larger maps, this method is much faster than GMAPCacher or downloading through MissionPlanner.

### Installation

[You can download QGIS from it's official website.](https://www.qgis.org/en/site/forusers/download.html#)
I recommend getting the LTS version, but it really shouldn't matter.

Next we are going to install a useful plugin, which lets us easily search for and open typical online web map services (like Google Maps, OpenStreetMaps, Bing Maps, etc.). Open the *Plugins* tab and click on *Manage and Install Plugins...*.
Search for QuickMapServices and install it.

### Usage

First create a new project in QGIS and set the project coordinate reference system (CRS) to WGS84 [EPSG:4326].

Open your preferred map sevice from the QuickMapServices plugin. You can search for it by clicking the following icon in the toolbar:

Now go to the region you want to download.

Open the *Processing Toolbox* and search for *Generate XYZ tiles (Directory)*.

You will have to provide the extent. For this click on the ... button either choose *Use Map Canvas Extent* to download everything thats on screen or *Draw on Canvas* to do exacty that. Input the minimum and maximum zoom levels you need (I recommend 18-20). There is no point in having zoom levels higher than 20, since the maps are not that high resolution and dowloading would take a long time. Change the *Tile Format* to JPG and the *Tile width* and *Tile height* to 100. Provide an output directory (create a new one) and optionally save the *Output html* to view the area you downloaded in a browser (you don't need this for the script).

Copy the zoom level folders to SD/IMAGES/yaapu/maps/qgis_default/ so the directory structure looks like this:
- `/IMAGES/yaapu/maps/qgis_default/18/*`
- `/IMAGES/yaapu/maps/qgis_default/19/*`
- `/IMAGES/yaapu/maps/qgis_default/20/*`

Select QGIS as the map provider on the script configuration menu and provide your zoom levels.

## Please make sure you have a valid GPS sensor in OpenTX telemetry page, if not please do a sensor discovery.
