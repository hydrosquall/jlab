# Making a map in Carto using geolocation data 

Making charts is one of the coolest things in data journalism. It is really a good way to visualize data about places, that sometimes it just won’t fit a normal type of chart. 

[Carto](https://voltdatalab.cartodb.com) is one of the best tools out there to do that. You can make interactive maps, download static image files and customize colors and points. And it is free if you are OK with using their more basic resources (which are good by most standards).

However, there are a few tricks in both better representing your data and making your map look good. 

This tutorial will teach you how to use addresses and geolocation with Carto, to visualize data the best way you see fit. 

For this tutorial you will need: 

1. [This dataset about mass shootings in the US](https://github.com/miguelpaz/jlab/blob/master/data/cartodb_mass_shootings_US.csv)
2. An account in [Carto](https://miguelpaz.carto.com)

___

## Understanding the dataset

The dataset we will use contains information about mass shootings in the United States during the first semester of 2016, and it has nine columns: 1. Date 2. State 3. City 4. Short address designation 5. Address 6. Latitude 7. Longitude 8. People killed and 9. People injured. The data comes from the [Gun Violence Archive](http://www.gunviolencearchive.org/reports/mass-shooting), a non profit organization that keeps an "online archive of gun violence incidents collected from over 1,500 media, law enforcement, government and commercial sources daily in an effort to provide  near-real time data about the results of gun violence".

For this tutorial, we have added the Address column and the LAT/LONG columns. 

Unlike the [Carto tutorial to create maps without geolocation data](https://github.com/miguelpaz/jlab/blob/master/cartodb_basics_tutorial.md), this dataset has information that can be displayed in many ways, as you will up next. 

Load the data in your Carto.

After you upload the .csv file, you will be brought to the `Map View` screen of your map, and you will likely see orange dots, displaying the LAT/LONG information of your dataset. 

![](https://github.com/miguelpaz/jlab/blob/master/images/map_cartodb_advanced_2.png?raw=true)

Give a name to your map in the `Untitled` area in the upper left corner and then go to the `Data View` as shown in the picture below: 

![](https://github.com/miguelpaz/jlab/blob/master/images/map_cartodb_advanced_1.png?raw=true)

Notice that the `geometry` field in the table displays the information you pointed out in the `LATITUDE` and `LONGITUDE` columns.

> **TIP:** In case you only have the address and not the LAT/LONG information, Carto can retrieve the information for you for free for up to 100 columns. For anything bigger than that, you will have to pay. If the number of addresses is not too large you can split the file into batches of 100 and then ensamble it all back together. If you don’t want to pay anything, [this awesome website](http://www.findlatitudeandlongitude.com/batch-geocode) will get the LAT/LONG in a batch for you. [This site](http://stevemorse.org/jcal/latlon.php) by Stephen P. Morse will also help you with batch geocoding (it also has a nice FAQ about address data). You can go also to [http://www.latlong.net](http://www.latlong.net/) to get the LAT/LONG information one address at a time. 

You can georeference your dataset in many ways, using city names, IP addresses, administrative regions, latitude and longitude data and city names. Since we have the actual addresses where the shootings occurred, it will be easy to georeference our dataset. 

Note that there is a `Short_Address` field, this is just in case you want to display that information separately, as the `Address` cells have the city and the state.

## Visualizing the information

Back to the “Map View”, you will see your orange dots. It is an accurate visualization by itself, but it could be better. In order for us to have a clear understanding of the information, it would be nice to have the State lines well delimited. To do that, we need what it is called **Polygons**.

Luckily, Carto gets information like this for free based only in the State name. But, since our dataset is already being used to show the dots in the map, we need to create a new layer.

To create a new layer, you need to click in the “+” sign located on the vertical tab in the right side of the screen, where the arrow is showing in the picture below: 

![](https://github.com/miguelpaz/jlab/blob/master/images/map_cartodb_advanced_3_arrow.png?raw=true)

We could import State borders information from a .csv file or other formats, but, conveniently, Carto has a nice community that makes this kind of polygon data available for free. 

Instead of clicking `Connect Dataset`, you can go to the `Data Library` option and look for the “USA States” data (be patient as the search tool is not as intuitive as others you may have tried before). Then, you can rearrange the order of the datasets by just dragging the right-sided column in the map view.

![](https://github.com/miguelpaz/jlab/blob/master/images/map_cartodb_advanced_4.png?raw=true)

## Customizing the map

Since we are only talking about the United States, maybe there is no need to have a basemap, as we already have the State lines delimited by our second dataset. 

To get rid of the basemap, just change it to a white background in the custom settings.

![](https://github.com/miguelpaz/jlab/blob/master/images/map_cartodb_advanced_5.png?raw=true)

Finally, lets customize the Map to better show the information, the colors and improve the interactivity. 

We can show the deadliest mass shootings in 2016 by using the “Bubbles” option in the `Wizards` section, using the `Killed` column as the main data, and then make it stand out as a dark red. 

![](https://github.com/miguelpaz/jlab/blob/master/images/map_cartodb_advanced_6.png?raw=true)

Then we will go to the `Infowindow` tab and enable the hover options for the tooltip. Try choosing the “Dark” hover scheme for a better visualization against the white background, and leave out the LAT/LONG columns, because whoever is seeing the map won’t probably care about it.

Select the other layer you are working with to change the default orange polygon fill of the States. For this tutorial we will choose the mid-dark blue.

There are several other customizations you can do to display your information. 

When you are done doing this, add a *Title* in the `Add Element` option, and it will give you the dataset title. In the `options` button in the bottom, you can make it a fixed title bar. 

Add the source of the data and go ahead to publish and share it! The result will be something like this:

![](https://github.com/miguelpaz/jlab/blob/master/images/map_cartodb_advanced_7.png?raw=true)



## Be a Pro

Try making a *heatmap* or customizing the *tooltips* with the `Infowindow Change HTML` functionality. 


#### How you can contribute 

*Do you have suggestions on how to improve this tutorial? Are there any broken links, typos or something else not working? You can contribute by opening a new issue.* 
