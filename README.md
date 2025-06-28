Final Report – Unity AR Gallery Project

This project was developed using Unity 6  with a focus on creating an interactive AR gallery where users can view 3D characters that appear next to paintings when recognized by the camera. The goal was to ensure that these characters are properly placed on the ground and always face the viewer.

We started by installing a few essential packages from the Unity Package Manager:

- AR Foundation: the core library for building cross-platform AR experiences  
- Universal Render Pipeline (URP): used to improve the rendering quality of the AR content  
- TextMeshPro: for displaying high-quality text descriptions next to characters

For image tracking, we added several painting images to the AR Reference Image Library. These images act as visual markers. Whenever one is detected by the camera, Unity triggers an event using ARTrackedImageManager. In our GroundPositioningHandler.cs script, we respond to this event by spawning a character model near the detected image.

To make sure the character is placed realistically on the ground and not floating, we detect the nearest horizontal plane using ARPlaneManager and place the character with a small vertical offset. This ensures good alignment even if the surface isn't perfectly flat.

Each character also comes with a floating text description. To make the text always readable, we added a LookCam.cs script to the canvas so it rotates to face the user. Similarly, the character itself uses RotateWithCam.cs so it always looks in the viewer's direction, but only on the horizontal axis (no awkward head tilts).

We also used a PlaneClassifier.cs script to ignore any planes that aren’t usable — like vertical walls or downward-facing surfaces. 

https://github.com/Nhd-github/XR_Gallary

This setup allows for a clean, responsive, and immersive AR experience, using a modular and well-structured codebase with scripts like GroundPositioningHandler.cs, LookCam.cs, RotateWithCam.cs, and PlaneClassifier.cs.
