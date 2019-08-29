# Argonaut
# Transport type
MKDirectionsTransportType
only _automobile_ and _walking_ are supported at the time for directions calculation. _transit_ is only supported for ETA calculations.

# Pitfalls
- Maximum size supported 4928
$0.size = .init(width: 4929, height: 4929)
-[MTLDebugRenderCommandEncoder validateFramebufferWithRenderPipelineState:]:1258: failed assertion `For depth attachment, the renderPipelineState pixelFormat must be MTLPixelFormatInvalid, as no texture is set.'

- Dark mode
if #available(OSX 10.14, *) {
                            $0.appearance = NSAppearance(named: .vibrantDark)
                        }

- Retina can only be modified on iOS
on OSX it is system default (always retina on)

- Timeout
-- Get ready for 20+ seconds delay
-- Has no rea timeout support, you have to implement it yourself

- Don't create a strong reference to shooter or it will lead to memory leaks

- Size should be multiple of 256, but sizes bigger than 2560 (10x) start having issues with rendering overlays. Maximum x is 19.
Optimal is 5

- Maximum valid in most cases zoom = 20 (21 only certain parts of the US)
- Minimum zoom mostly 5, but sometimes also 4

- You want to use a bigger image and cropped otherwise the annotations won't render properly and it will look with considerable bad quality

- Although it is convenient to use MKRoute as is you will soon find that not being able to modify it, hence, recreate it, it is better to generate your own structs or models, specially if you want to persist and share this routes.

- The ratio of map points to coordinates is: 1048575
as in: 1 / (Double(1 << zoom) / 1048575)) * 256


# info.plist
From all the keys, the one that you need to setup in MacOS is: NSLocationUsageDescription
This one is deprecated in iOS, but is the only one supported on MacOS 10.14+

for iOS 8-10: NSLocationAlwaysUsageDescription
11+: NSLocationWhenInUseUsageDescription

Important to have at least those 2 for backwards compatibility

# Backward compatibility
- Apple maps iOS 10+
- Google maps iOS 10+

# In iOS 13 maps are constantly animating according to its container size, which could cause crashes if you animate the container and then release it



# mapView(_:didUpdate:)
mentions:
userLocation
The location object representing the user’s latest location. This property may be nil.

But in swift is not optional, hence you can't compare against nil. Nevertheless I have seen it fail, so let's be safe and validate with coordinate, which is optional

for some reason I never got heading updates on MKUserLocation so needed to implement it with location manager


# MKMapSnapshotter
It didn't work on the simulator for iOS 11 and the first versions of iOS 12
In iOS 13 seems to not be working, just displays a black screen, both in light and dark modes