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

- Maximum zoom = 20

- You want to use a bigger image and cropped otherwise the annotations won't render properly and it will look with considerable bad quality

