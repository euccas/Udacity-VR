# Project 2: Modern Apartment

## Environment

* Google VR SDK Version: 1.0
* Deployed to iPhone

## Lighting

* I added a direct light (sun), a few area lights and spot lights. However, the lighting looks unchanged in the scene when I rotate the lights.
* Set all lights except for the direct light to be **Baked**.
* Set the **lightmap** configuration according to the instructions in project review rubric.

## Animation

* Added the animation to the Globe. I unchecked the "Loop" in the Animation Controller (Globe) to make the Globe rotate only once when the button is clicked (triggered)

## The Challenging Part

* I spent some time and efforts to positioning the objects in the scene so they don't look "floating". What I did was zooming in the scene to look at the details of the objects, and look at from different perspectives to make sure they are at the expected positions.

* The lighting part was challenging. In the first time when I worked on the project, the lighting disappered from the scene, although I didn't know exactly what operation caused that. Even after adding a direct light and a few area lights, the scene still look dark (not as light as it was in the starter project). In the end I created a new project and built the apartment again.

* Animation: I tried to add the animation to the clock's handles. The animation doesn't take effect in the "Game" view. Then I found that was because the clock's handle was set as "Static". Only unstatic objects can have animations.
