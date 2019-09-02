# Offline maps and navigation

# Agenda
- Problem
- Solution
- Implementation
- Related work
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

## Drawbacks
- Needs to be online first
- Uses memory storage
- Might not be free (provider)
- No real time