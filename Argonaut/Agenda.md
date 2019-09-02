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
- What can we add

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

