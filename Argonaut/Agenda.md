# Offline maps and navigation

# Agenda
- Problem
- Solution
- Implementation
- Conclusions

# Problem
- BVG, official app for public transport in Berlin.
We don't know what options we have.
-- Train stations
-- Which one is closer
-- How do we go to from a known location to another
-- We can see a map

- Northern, app for trains in the United Kingdom.

>>> We have transport apps as example, but we can apply this same logic to any app depending on locations, navigation, or maps.

# Problem
We make apps that navigate you, if you are online.

## Overlooking
- Traveling abroad
- Bad signal
- You don't want to use your mobile data

## But also
- You don't have a subscription

>>> Mobile Internet is not equally accessible to everyone.

>>> According to the United Nations, there were less than 60 mobile data subscriptions in 2017 per each 100 worldwide. No newer information available yet.

>>> ITU (International Telecommunication Union)
by the United Nations

>>> LCDs (Least developed countries)


## What could we do?
- Have static information
-- Stations
-- Schedules (maybe)
-- Points of interest
   (Aberystwyth Castle)
- Use your location to estimate
-- Points of interest close to you
-- Distance to those points
-- Should you turn left or right
   (heading)
- Store maps
-- Show where you are
- Store directions
-- From and to points of interests
-- On demand

# Solution
We can can navigate you,
even if you are offline.

- How does it work online
- What is usable offline
- What can we store

## How does it work online
- Components of navigation
- Interactions
- Flow

## Navigation
- GPS
- Maps
- Points of interest
- Directions

## GPS
Global Positioning System,
maintained by the US government,
it is free and open

>>> There are other positioning systems but GPS is the most widely available.


## GPS
Satellites acting as beacons that devices can listen to calculate their own latitude and longitude.

>>> It is common to associate navigation with GPS, as we can see from the home page of gps.gov

>>> The problem is not GPS! GPS is not the map.

>>> GPS only gives you the position of the blue dot, not the map.

>>> Your device gets the signal from the satellites and can tell you where you are.
You are theoretically in the range of vision of at least 4 satellites at all time, anywhere in the world.
It is theoretically because the signal is quite weak and if you are underground or indoors you might get different results.

## Map
Set of images that we can associate with a region
- Computer generated images
- Satellite imagery
- Aerial photography
- Vector rendering

## How a map looks
>>> This is how we usually see maps, a continuous visualisation of a area

## What a map actually is
>> This is how it actually works

Each image represents a region with a certain amount of detail
The smaller the region, the more detail you could add

## Region
A geometrical representation of the world in 2d.
A rectangle from this coordinate to this other.

## Providers
- Apple Maps
- Google Maps
- OpenStreetMap
- Here
- TomTom

## Point of interest
Information associated with a location.

## Location
- Latitude (north - south)
- Longitude (east - west)

## Aberystwyth Castle
Location:
   Latitude: 52.4135223
   Longitude: -4.0880009
Description: 13th-century seaside
   fortress, built by Edward I
Address: King Street, Aberystwyth
   SY23 2AU, Wales

## Directions
How to go from a point of interest to another.

From Aberystwyth University to the Castle

A route consisting of a set of coordinates to pass when traveling between 2 locations.

## Can also contain
- Distance
- Expected duration
- Type of travel
   Walking
   Driving
   Cycling

And indications specific per point in the route.

- Here turn left

## Interactions

>>> A map consists of images associated with coordinates
>>> Points of interests are information associated with coordinates
>>> Directions is information associated with coordinates

## Flow

>>> Your device receive its location from the GPS, then an app can request information for the region around itself from its provider. Finally, it displays images of the map in the region, with points of interest nearby and probably a blue dot representing itself.

## On demand

>>> You select a point of interest you want to go and the app requests directions, its provider returns a route and information, and the app can display lines and gives you instructions.

## Offline
- Your location
- Area around you

## Online
- Images
- Points of interest
- Routes

## But these are static
- Images
- Points of interest

>>> Rarely a point of interest changes, and images for maps get updated every few years.


And routes between to known points of interests are also static*

- Without real time information like traffic and construction works.

## What can we store
- Maps important for our app
- Maps requested by you
- Points of interests for our app
- Directions between points
- Directions requested by you

>>> If we have an app that helps you get around Aber we could store directions between the train station and the castle, because we know that most people would want to visit it.

>>> And maybe you could request the app to store directions between the train station and the university, because you know you will want to go there.

## Disadvantages
- Uses memory storage
- Might not be free (provider)
- No real time

# Implementation
- MapKit
- Map
- Points of interests
- Directions

## MapKit
Cons
- Google Maps is more popular
- Not as detailed.

Pros
- Out of the box (import MapKit)
- No quota limit

# info.plist
iOS 8 - 10
NSLocationAlwaysUsageDescription
iOS 11+
NSLocationWhenInUseUsageDescription
macOS 10.14+
NSLocationUsageDescription

In Xcode 10 or below you need to
enable Maps capabilities.
No longer necessary in Xcode 11.

For macOS you also need to enable
access to location in capabilities.

## Map

MKMapSnapshotter
- iOS 7+
- macOS 10.9+

>>> In order to interact with MKMapSnapshotter you need to create a MKMapSnapshooter.Options, set the map rect you
want to be captured, instantiate the shotter with it, and call start.

>>> You will receive a response asynchronously with an optional MKSnaposhotter.Snapshot and an optional error.

>>> You can then retrieve the image from the snapshot, if everything went well. And store it, for example.

>>> Now, when dealing with MapRects is when it gets tricky.

## MKMapRect
2d representation of the curved surface of the globe.
Often used to show the entire surface of the globe all at once.

But, before using MKMapRect we need to understand
- MKMapPoint
- Size of the world
- Zoom level

## MKMapPoint
This data structure represents a point on the map.
You can create them with coordinates, perform calculations with them and convert back to coordinate values.

The entire surface of the globe,
in points is

>>> 268,435,456 points
>>> Which we can check by printing MKMapRect.world.size

## Zoom level
We can use a z coordinate or zoom level to define how close or far we want to generate or map images.

If we want to display the whole world at once,
in a just one image, we could call that
a tile at the position
x: 0
y: 0
z: 0

Zoom 1 divides zoom 0 into 4 tiles
And zoom 2 divides each tile of zoom 1 into 4 again, and so on.

If we want our image to be 256x256 pixels
that would mean we can have 20 zoom levels, or:

>>> log2(MKMapRect.world.width / 256)

And the size of tiles in map points:

>>> MKMapRect.world.width / pow(2, zoomLevel)

256x256 is the default for MKMapSnapshotter
and is also the standard with other providers.

That also means we would need to have
4^20 or 1,099,511,627,776 images at the
maximum zoom to display the whole globe


Aberystwyth castle
x: 131166208
y: 88162304
z: 16
size: 4096
>>> Size is in map size

To use these tiles in our MKMapView

Assuming we saved every tile with a name like
x_y_x.png in the folder myFolder, for example:
myFolder/1_0_1.png

In our MKMapViewDelegate


## Points of interest

We could store those relevant
to our app.

User's location will be shown, if granted permission, and don't store it.

We can also let users select places they want to store.

## Directions
Once they are stored

Things to consider
- When creating a snapshot it might take up to 20 seconds to respond, and there is no timeout support.
- You have to create a different MKMapSnapshotter for each image.
- Size of the images should be divisible by 256, but preferably smaller than 2560. And the maximum supported is 4928.

# Conclusions

- Hope we can add more support for offline mode
- Look for Argonaut in the AppStore (iOS and macOS)
  it is free and OpenSource
https://github.com/oinkhub/argonaut