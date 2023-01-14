# TUTORIALS
## WEEK FOUR-PRESSURE PLATES

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

#### USING RIGIDBODY:

Create 2 diferent coloured game objects and attach rigidbody components to both so that the player object can move them around. These will be the key objects that will be placed on the corresponding pressure plates.

Also create 2 thin game objects placed on the plane. These will be the pressure plates that will be interacted with to open doors. To not confuse things, set the colours of these pressure plates to match the colours of the key game objects.

Create 2 more gameobjects that will be the doors that open when the key object is placed ontop of the pressure plate object. Attach rigidbody components to both of these doors as well.

Now, create a C# script called "DoorController" and attach this script to both Key objects. In this script create a public bool variable called "DoorOpen" and set it to false as the door should not be open to start with. Also, create a public GameObject variable called door and drag the door object into this variable assignment in the Unity editor. Finally, creat one last public variable called doorSpeed and set it as a float.

Now, create a new function called OnTriggerStay. This means that if the Key object collides with the desired collider and stays, the following actions will happen that are in this function. 

In this function, create an if statement to check if the variable doorOpen is equals to false. If it is, we need to create another if statement to check if the Key object is colliding with the correct collider. We can do this by comparing the tag of the collider object as shown below.

![Screenshot 2022-12-10 171003](https://user-images.githubusercontent.com/114989045/206866930-52e94e16-0fd2-433b-8be8-25f9824df1c5.png)

To make this CompareTag fucntion work, we have to go back into the Unity editor and create a new tag called "PressurePlate" and assign the pressure plate objects to this tag.

In the if statement, we want to finally open the door after all of these checks. We can do this by getting the rigidbody component on the door and adding a force to it.

![Screenshot 2022-12-10 171019](https://user-images.githubusercontent.com/114989045/206866936-63e5bac8-3634-4de9-af4e-a5f21927d4e7.png)

As shown above, we can put a direction of force and a speed in that direction, and a type of force, e.g. a continuous force or impulsive force.


#### USING TRANSFORM:

Create 2 diferent coloured game objects and attach rigidbody components to both so that the player object can move them around. These will be the key objects that will be placed on the corresponding pressure plates.

Also create 2 thin game objects placed on the plane. These will be the pressure plates that will be interacted with to open doors. To not confuse things, set the colours of these pressure plates to match the colours of the key game objects.

Create 2 more gameobjects that will be the doors that open when the key object is placed ontop of the pressure plate object.

![Screenshot 2022-11-24 211543](https://user-images.githubusercontent.com/114989045/203864018-7cb6d907-68c5-4d89-b2f6-0b54d8722ed6.png)

Lastly, as shown in the image above, create duplicates of these doors, switch off the mesh and colliders for these objects, and name one "DoorOpenPos" and the other "DoorClosePos" for both doors. These will be the positions of the doors when opened and closed.

Now, create a C# script called "DoorController" and attach this script to both doors. In this script create a public bool variable called "openDoor" and set it to false as the door should not be open to start with. 

Create 2 more public variables which will be Transform variables. This means that the variable is using the transforms (position, rotation, etc.) of the selected game object. Name these 2 Transform variables "doorOpenPos" and "doorClosePos". 

In the Update function, create an if statement to check if "openDoor" is equal to true. If it is, then we are going to move the door that this script is attached to, to where the "doorOpenPos" object position is. We can do this by using transform.position as shown below.


![Screenshot 2022-11-24 214149](https://user-images.githubusercontent.com/114989045/203866472-e9430924-3bc8-48e6-b0f8-6ff71b720458.png)

We also have to create an if statement to say when the door is not open. This is essentially the same if statement as before, however, it is checking if "openDoor" is equal to false and setting the position of the door to the same as "doorClosePos".

![Screenshot 2022-11-24 214550](https://user-images.githubusercontent.com/114989045/203866814-6fcedf6d-288a-4191-a92d-31d68ec41ca8.png)

Now in the Unity Editor, we have to drag the game objects that we created for the open and close positions into the public Transform variable slots for "doorOpenPos" and "doorClosePos".

![Screenshot 2022-11-24 214839](https://user-images.githubusercontent.com/114989045/203867151-18b607b9-0fac-4e8a-a48f-8ac8733cbe4f.png)

To trigger this transform of opening the door to doorOpenPos, create a new C# script called PressurePlateTrigger and attach it to both pressure plates. 

Create a public variable that is referencing the DoorController script we created earlier with the transforms called DoorControllerScript.

Create a new function called OntriggerEnter. This means that if the Key objects collides with the desired colliders, the following actions will happen that are in this function. 

in this function, create an if statement to check if the Key objects are colliding with the correct colliders. We can do this by comparing the tag of the collider objects as shown below.

![Screenshot 2022-12-10 202302](https://user-images.githubusercontent.com/114989045/206873983-da777826-d029-4bb6-88e7-91149a892117.png)

To make this CompareTag fucntion work, we have to go back into the Unity editor and create a new tag called "PressurePlate" and assign the pressure plate objects to this tag.

If it is the correct tag of "PressurePlate", the variable DoorControllerScript will pull the boolean variable DoorOpen from the DoorController script and set it as equal to true.

Now, we need to create another function quite similar called OnTriggerExit. This function means that when the Key objects leaves the collisions, the following in the function will happen.

In this function, create an if statement to check if the objects exiting the collisions has got the tag "PressurePlate". If it has, the variable DoorControllerScript will pull the boolean variable DoorOpen from the DoorController script and set it as equal to false.

![Screenshot 2022-12-10 202313](https://user-images.githubusercontent.com/114989045/206873985-cbcd70cc-989d-49d4-86f3-ad9c0285d02d.png)


#### TEMPORARY OPEN KEY:

To add to this pressure plate door, we can make the door open for a set time when the key is placed on the plate and then close after that set time. 

To do this, we can use the two scripts we created previously for moving the doors using transforms: PressurePlateTrigger script and DoorController script.

Open up the DoorController script and create 2 more variables, one public float called timeRemaining and one public boolean called timerIsRunning. Set the value of timeRemaining to 5f.

![Screenshot 2022-12-10 203649](https://user-images.githubusercontent.com/114989045/206874395-0d1b96d2-1e90-424c-b97f-66ee98fa71f9.png)

Create a new function called StartTimer and inside this function, create an if statement to check if timeRemaining is more than 0. It will be as the timeRemaining is set to 5f, therefore, the door can be opened. 

We can move the line of code shown below in the Update function to this if statement we have just created like so:

We also need to start counting down when the door opens. This is done by subtracting Time.deltatime from timeRemaining.

If the variable timeRemaining is not more than 0, than we need to set the timerIsRunning variable to false. we also need to move the position of the door back to the close position as shown below:

![Screenshot 2022-12-11 200215](https://user-images.githubusercontent.com/114989045/206926103-bc882289-e86d-4864-9886-dfa5c97ef8ae.png)

Now, we need to reset the timer back to the 5f value as when the key object is moved off the pressure plate, the timer needs to reset, otherwise, it cannot open again.
