# VR Unity3D Project Notes

## Project 2 - Modern Apartment

### How to add Cardboard functionality to your scene?

Three steps:
1. Build VR Camera
2. Implement head rotation
3. Implement the GVR SDK

### Build VR Camera

* Create two Camera objects, one for the left eye, the other for the right eye. You can group the two Cameras under one GameObject.

* Set each Camera's viewport properties
** For the left eye, set its viewport width (W) to 0.5
** For the right eye, set its viewport x coordinate to 0.5, and the viewport width (W) to 1

* Set each Camera's X position according to cardboard's LSD (Lense Separation Distance) value
** Measure the LSD of the cardboard. For example, the LSD of your cardboard is 64mm.
** Divide the LSD by two, you get the distance between the nose to one eye. You need move the two Cameras with this distance.
** For the left eye Camera, set Position X = -0.32
** For the right eye Camera, set the Position X = 0.32

### Implement Head Rotation

* Create a C# script (eg. HeadRotation.cs)
* Update Start() function, enable Gyro

```
Input.gyro.enabled = true;
```
** Update Update() function, get data from Gyro every frame

```
Quaternion att = Input.gyro.attitude;
att = Quaternion.Euler (90f, 0f, 0f) * new Quaternion (att.x, att.y, att.z, att.w);
transform.rotation = att;
```

* Apply this C# script to the Camera
Add "Script" component to the Camera group, or to each camera. Select the "HeadRotation" script in the added "Script" component.

### Implement the GVR (Google VR) SDK

* Add GVRViewerMain prefab in your scence. The prefab is located in GoogleVR > Prefabs
* Add a normal camera in the location you want to view from **Deactivate** the VR Camera system

Usage of GVR SDK
* GVR has some built in tools for making it easy to test your application without having to deploy to your phone.
* To control the rotation of the head in the editor, use **Alt** and **move the mouse** to rotate in the **XY** direction
* To control the Tilt (which is rotation in the **Z** axis), use **Ctrl** and **move the mouse**

### Create Animation



