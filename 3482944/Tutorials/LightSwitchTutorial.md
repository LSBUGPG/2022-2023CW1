## 1 Creating our scene

https://www.youtube.com/watch?v=FhMuL70xLus

To start off I have created a default 3D unity scene and made a simple "Lamp" that can act as our switchable object. (For me, I have simply used a cube).
And have imported the 3rd person character controller from the asset store.

https://assetstore.unity.com/packages/essentials/starter-assets-third-person-character-controller-196526

Start out by opening the `Playground` scene in the editor, this willl give you a character and controller to work with and a small scene where you can place your lamp.

![alt text](https://i.imgur.com/zh2COIq.png)

On your lamp, make sure you have a collider that is set to `Is Trigger` on the object, and make it so that it is the range of how far you would like the player to be to activate the light. (I have used a sphere collider)

![alt text](https://i.imgur.com/pQpyQ3l.png)



## 2 Creating our script

In your unity editor create a scritp and call it `TurnLight` the script is as follows, annotated to make it easier to understand what each line is doing. 
![alt text](https://i.imgur.com/DVaycw3.png)


## 3 Adding our light

Within your lamp item create a point light, this is what we will use with the script to actually be our light within the cube, so align it with your cube and set its settings to be how you want it to look when turned on.

Apply the `TurnLight` script to your lamp object, and put your light into the light variable slot.

![alt text](https://i.imgur.com/tjHfC8O.png)

## 4 Test it out

This should all now work, if you play your scene, move into your sphere collider and press E, your light should turn on and off.

I took a small amount of time to make sure that the sphere collider was the right size now and that my light was in the correct place and colour.

![alt text](https://i.imgur.com/wU8Fb6U.png) 
![alt text](https://i.imgur.com/rphyCkN.png)
