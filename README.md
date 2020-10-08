# Introduction

This code-through will show how to take open data addresses and turn them into an interactive map using the **[Leaflet](https://cran.r-project.org/web/packages/leaflet/index.html)** package. I will take addresses from the Phoenix Public Library system and plot these on a map, with markers that provide additional useful information about the libraries. The goal is to have a single page where people can go to find which library would be most useful to their needs. This map could also be embedded on the public library website to inform patrons. 

<br>

## Inspiration & Help

This project built on information in a [**Towards Data Science**](https://towardsdatascience.com/making-interactive-maps-in-r-with-less-than-15-lines-of-code-bfd81f587e12) Medium post by Brandon Walker. 

## Data

These maps were built using data from the [**Phoenix, AZ Open Data Portal**](https://www.phoenixopendata.com/dataset/libraries/resource/b7158429-b69e-4f87-8a96-b4857c6d65b5). The data was not linked through the API (since it was broken at the time of creation) so the data is static as of 10/1/2020.

```{r setup, include = FALSE}

# SET UP GLOBAL OPTIONS

knitr::opts_chunk$set(
	eval = FALSE,
	fig.width = 10,
	message = FALSE,
	warning = FALSE,
	include = FALSE
)
```
# Preprocessing

The data from this portal is fairly minimal and requires very little preprosessing. For **[Leaflet](https://cran.r-project.org/web/packages/leaflet/index.html)** to work properly, we need more than just the address of the library - which is provided in the dataframe under `libraries$AddressFull`.

## Adding the Lon/Lat Coordinates

```{r}

```
<br>

## Geocoding with GGMAP

We have a series of addresses and X/Y coordinates that correspond with longitude and latitude. However, if you did not have lon/lat coordinates, you can load [ggmap](https://cran.r-project.org/web/packages/ggmap/index.html) package and call the `geocode()` function to the addresses.

For example, if I wanted to find a central location in Phoenix, AZ as the center of my map (we'll adjust the zoom later). I can chose the [Burton Barr Library](https://www.phoenixpubliclibrary.org/Locations/BurtonBarr) and pass the address through `geocode()` like this:

```{r}
geocode("1221 N. Central Ave, Phoenix, ArZ 85004")
```
<br>

# Creating and Customizing Our Map

## Adding Markers for the Libraries

The purpose of this map is to show where all of the libraries are located, so we want to add markers. You can add basic blue markers by calling `addMarkers()` in Leaflet and then adding the lng/lat coordinates. You can also pass it through a dataframe if you have a list of coordinates.

```{r}
libmap <- leaflet() %>%
  addMarkers(lng = libraries$DegreesX, lat = libraries$DegreesY) %>%
  #setView(lng = XXX, lat = XXX, zoom = 13)
```

<br>

## Adding Popups with Information

To make our map more useful, we'd like some basic information to popup when the user clicks on a marker.  I've chosen the library's website because I feel like that would lead the user to discovering all of the information that they need (from books to lending policies). This information is provided in the dataset so we can link to it using `libraries$PlaceWeb`.

```{r}

```


<br>

## Other Misc Features

This map is only being used for a single purpose: finding PHX libraries. I don't anticipate that people will use it to look up other locations around the globe so I'm going to lock the panning and zoom functions (to prevent people from accidentally navigating far away or looking for libraries in other counties).  To do that I set the `dragging = FALSE` (panning) and locked the zoom between 14 and 18.

```{r}

```

# Final Product

