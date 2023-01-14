# TUTORIALS
## WEEK 3-ENLARGE PLAYER PICKUP

#### PLAYER CONTROLLER:

Create a player object and a plane.

Then, create a C# script called PlayerController and attach it to the player object.

In this PlayerController script, above the Start function, create a public float variable called speed. Creating this as public means that we can input and edit this value in the Unity editor.

In the Update function, create 2 local float variables called h and v. 

![Screenshot 2022-11-04 201036](https://user-images.githubusercontent.com/114989045/200065791-53ea03ba-88bf-4ca1-b717-a404b6985ffa.png)

As shown in the image above, these 2 variables are set as the inputs from the user. Input.GetAxis means that it needs 2 input values that are opposites. Horizontal gets the horizontal arrow keys (left and right) and vertical gets the vertical arrow keys (up and down).

Next, we need to use these input values and move the player object based on the float values. transform.Translate does this. By putting the variable h in the x co-ordinate and v in the z co-ordinate, this moves the player object in the direction of the floats inputted by the player.

This movement needs to have a speed so multiply these co-ordinates by the variable speed.

I have also put in a jump input shown below, however, you do not need this for this tutorial.

![Screenshot 2022-11-04 201102](https://user-images.githubusercontent.com/114989045/200065804-820af291-4bf4-46c4-be8b-e0d32bc192ef.png)


#### INCREASE SIZE:

Create an empty object called controller, and attach a script to it called PlayerSizeController. 

Now create 2 public variables, one that is a GameObject called PlayerPicked that will be the player object, and one that is a boolean called timerIsRunning. Also create a private float variable called timeRemaining and set it equal to 5f.

Create a public function called StartTimer. This function will be called when timerIsRunning is equal to true. In this function, create an if statement to check if timeRemaining is more than 0. if it is, we have to increase the player object's scale by using transform.localScale as shown below:

![Screenshot 2022-12-12 102124](https://user-images.githubusercontent.com/114989045/207021615-9a74ea6b-63bb-48c7-8b72-dff135d154a6.png)

We have increased the scale values to 10 in each axis with Vector3. We also need to decrease the timer float timeRemaining by Time.deltaTime as this is what counts down the seconds.

If timeRemaining is not more than 0, we need to set timerIsRunning to false as this means that the countdown has reached 0. We also need to set the scale of the player object back to 1 in all axis using transform.

![Screenshot 2022-12-12 102706](https://user-images.githubusercontent.com/114989045/207022708-269516f7-215d-4c5b-9ac2-ce11e99d8316.png)

Next, we need to actually make sure the player object collides with the pickup object and triggers this StartTimer function. Create a new script called PickupDrop and create a public variable referecning the PlayerSizeController script we had just created earlier. Name this layerSizeControllerScript.

In this script, we need to create a new function called OnTriggerEnter which will perform whatever is in this function when the specified collision is triggered on enter.

In this function, we need to check that it is definitely only happening if the collider is triggered by the player object. This is done by using tags. Go back into the Unity editor and create a new tag called "Player" and assign the player object with this tag.

Now, back in the script, we can use CompareTag to check it is the correct one. When the tag is correct, we want to destroy the pickup object on collision and start the StartTimer function in the PlayerSizeController script.

This is done by referencing the timerIsRunning boolean variable in that script and setting it to true.

![Screenshot 2022-12-12 103629](https://user-images.githubusercontent.com/114989045/207024583-8e321e14-8dbc-4827-9880-c79c7e5d9a2a.png)

Going back to the PlayerSizeControllerScript, in the update function, we need to call the StartTimer function.
