# robotDevastation-openrave-models

[Robot Devastation](http://asrob-uc3m.github.io/workgroups/2017-05-28-robot-devastation.html) OpenRAVE models.

## How to generate simulated QR codes ([ref](https://github.com/asrob-uc3m/robotDevastation-openrave-models/issues/4#issuecomment-373781813))
1. Only once:
   1. Install https://github.com/welshjf/blender-local-qrcode via the .zip methid (clone --recursive, then run bundle.sh). Add and enable in Blender.
1. In Blender:
   1. Generate code: Add > Mesh > QR code.
   1. Modify `data`, leave invert unchecked (and fixed size and join blocks fixed), change Error correction to L.
   1. Move around, using snap to grid (and `ctrl` for descrete movements), create box behind, separate a bit.
   1. Via materials (small sphere on right), set colors of object (white) and cube background (black).
   1. Exported to `.x3d` format (direct export of `.obj` appears empty in OpenRAVE).
1. In Meshlab, import, then exported to `.wrl`.
1. The generated file can be rotated and moved within OpenRAVE XML.
