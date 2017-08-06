# VR Unity3D Project Notes

## Project 2 - Modern Apartment

### How to add Cardboard functionality to your scene ?

Three steps:
1. Build VR Camera
2. Implement head rotation
3. Implement the GVR SDK

#### 1. Build VR Camera

- Create two Camera objects, one for the left eye, the other for the right eye. You can group the two Cameras under one GameObject.
- Set each Camera's viewport properties
  - For the left eye, set its viewport width (W) to 0.5
  - For the right eye, set its viewport x coordinate to 0.5, and the viewport width (W) to 1
- Set each Camera's X position according to cardboard's LSD (Lense Separation Distance) value
  - Measure the LSD of the cardboard. For example, the LSD of your cardboard is 64mm.
  - Divide the LSD by two, you get the distance between the nose to one eye. You need move the two Cameras with this distance.
  - For the left eye Camera, set Position X = -0.32
  - For the right eye Camera, set the Position X = 0.32

#### 2. Implement Head Rotation

- Create a C# script (eg. HeadRotation.cs)
- Update Start() function, enable Gyro

```
Input.gyro.enabled = true;
```

- Update Update() function, get data from Gyro every frame

```
Quaternion att = Input.gyro.attitude;
att = Quaternion.Euler (90f, 0f, 0f) * new Quaternion (att.x, att.y, att.z, att.w);
transform.rotation = att;
```

- Apply this C# script to the Camera
Add "Script" component to the Camera group, or to each camera. Select the "HeadRotation" script in the added "Script" component.

#### 3. Implement the GVR (Google VR) SDK

- Add GVRViewerMain prefab in your scence. The prefab is located in GoogleVR > Prefabs
- Add a normal camera in the location you want to view from **Deactivate** the VR Camera system

Usage of GVR SDK
- GVR has some built in tools for making it easy to test your application without having to deploy to your phone.
- To control the rotation of the head in the editor, use **Alt** and **move the mouse** to rotate in the **XY** direction
- To control the Tilt (which is rotation in the **Z** axis), use **Ctrl** and **move the mouse**

### How to add Animation to the objects ?

1. Select the object, create an "Animation" in the Animation window.
2. The animation clip is similar to Adobe Flash, it uses keyframes and interpolations.
3. Unity will generate an "Animation Controller" for the created animation. Open it in the "Animator" window to change the state machines, apply triggers.
4. Add the Script for controlling the animation triggers in the Object's property.

How to delete a transition in the Animation State Machine?
- The "delete" option doesn't exist in the context menu (right click), the way to delete a transition is in the **Inspector** window, below the bright grey area on the right where it reads "Transition, Solo, Mute", is a **minus symbol**. Clicking it removes the transition.

### How to light the scene?

Types of lights:
- Directional light (the sun): As Directional Lights do not have a source position, they can be placed anywhere in your scene without changing the effect of the light. Rotating the light however does greatly affect the visual result.
- Area light
- Spotlight
- Point light

Reference: [Unity3D light types](https://unity3d.com/learn/tutorials/topics/graphics/light-types?playlist=17102)