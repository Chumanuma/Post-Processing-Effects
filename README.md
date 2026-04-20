# Post-Processing Effects

Controls for different effects:
Number keys at the top of the keyboard, HOLD the button to maintain the effect as releasing the key will cease the effect.
1- Chromatic Aberration
2- Bloom
3- Depth of Field
4- Color Grading
5- Lens Flare (Look at the sun)

Place some shapes around the level, I make a landscape with grass and simple shapes that come with Unreal Engine, I applied the same rock texture with different types of surfaces on each of them (smooth, porous, rough, etc) as well as the actual rock that the texture was meant for.

Grass is optional but I felt it added more detail and you can see how effects react to the different tiny shapes

The blueprints I created can be copy and pasted for a good portion with some tweaking

the effects themselves are in the top left in your character blueprint
<img width="327" height="376" alt="image" src="https://github.com/user-attachments/assets/fcc131fe-a919-41c4-ac03-1d5572704829" />

You just add a post process for however many effects you wish to add and customize each one on the right side in details for what you want the effect to be.

Then make sure ALL of them have blend weight set to 0.0 to essentially make non-existent

Here is the blueprint you must craft next:
<img width="1331" height="462" alt="image" src="https://github.com/user-attachments/assets/0ebd3921-3dfc-45a8-9cc8-8f05261f6a35" />

This is essentially drawing from an array of post process component class then changing the blend weight.
The yellow node "PostProcessRemoveValue" is a timeline node for fading the effect in and out.
Create a timeline track with a length of 1 and proceed to make a point at 0 and 1 exactly.
Select both points and right click one of them, then click User so that the line is curved. Timeline example below:

<img width="1634" height="480" alt="image" src="https://github.com/user-attachments/assets/e6ec7342-4cc8-4d9f-b37d-3987f945250f" />


You can copy and paste for most of the next two blueprints:
<img width="1310" height="405" alt="image" src="https://github.com/user-attachments/assets/a6755da7-58ad-46aa-8409-c5826be607fc" />

The one above is the same thing with some name changes and a lerp node to go back to 0 when the blend weight is 1.
Self explanatory, but it will remove the effect when all is said and done.

The third blueprint is this one below:
<img width="1470" height="589" alt="image" src="https://github.com/user-attachments/assets/64880178-caa2-4d23-8976-a679ea5112b4" />


The third blueprint is to clear all post processes on the actor then checks if the blend weight is higher than 0 in which case it will return to 0.

If everything is working after compile, then move on to the binds.

<img width="851" height="444" alt="image" src="https://github.com/user-attachments/assets/054e62a9-19da-4298-955d-2845e5998cd1" />

The above image is my blueprint for the first effect, all of them follow this blueprint but you just change the post process (dragged in from the components) and the keyboard event in this case, the number 1 next to tilda.

You can copy and paste this blueprint with the necessary changes and each individual effect in components to achieve a applicable version of each one. You could apply this logic and the setup to a single character type of game, but may want to organize the post processes in a better manner if they must act beyond a single actor. 



