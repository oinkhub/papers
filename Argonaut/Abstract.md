# Abstract
Navigation apps often rely on an Internet connection. Sometimes, when you most need it, this connection is not available or just fails. It is possible to provide maps and navigation without Internet. Preparing your app for offline use could dramatically improve your users experience.

# Offline maps and navigation with MapKit

# Argument
## Problem
- Apps often overlook providing navigation when offline.
- It is so easy to rely on applications to navigate, but quite so often as developers we fail to remember there is no guaranty that an Internet connection will be available.

You are visiting a foreign country, don't speak the language, and your Internet provider doesn't exist here. An important meeting is scheduled in a few hours and you just have to make it.
If you previously saved an offline map with Google Maps you might get directions, but the general experience is not the same as when online, the level of detail is greatly diminished, and you can't control the are where you want the map to be saved, rather it saves large areas even though you might just want a smaller portion of it.
If you didn't save previously an offline area you might still have the fortunate of Google Maps caching the last areas that you where viewing in the app. It is not perfectly clear how the cache is managed and you don't have any kind of control over it.

If using Apple Maps then it is a bit harder, this app also caches last spots you viewed, mostly on areas zoomed out, but it has no option to save for offline use.