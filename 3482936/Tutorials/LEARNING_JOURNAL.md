# LEARNING JOURNAL

### TASK ONE-TURRET

**PROBLEM:**
I did not know how to get the turret object to rotate in the direction of the player. I knew it was to do with transform, however, I did not know what rotation function was needed.

**SOLUTION:**
I decided to go onto Unity Docs and search rotate. I had a scroll of all the rotate functions until I came across transform.LookAt: https://docs.unity3d.com/2021.3/Documentation/ScriptReference/Transform.LookAt.html
I then followed the instructions to create the turret movement

![LookAt](https://user-images.githubusercontent.com/114989045/199606018-f4c53f24-c196-4222-9ff1-ef51b5c021f9.png)


**PROBLEM:**
When the player moved around the turret, the barrel of the turret was facing the wrong direction. The barrel need to be facing towards the player as this would be wear the bullets would appear from.


**SOLUTION:**
I opened the turret prefab and rotated the cylinder barrel round to the opposite side of the capsule body.

![Turret](https://user-images.githubusercontent.com/114989045/199606095-893c2e65-0ba8-4a49-8916-76f61141d718.png)


**PROBLEM:**
I knew that I had to use Instatiate to create the bullets, however, I also needed the bullets to move at a high velocity in a forward-facing direction. I did not know how to do this.

**SOLUTION:**
I opened up Unity Docs again and searched up Instantiate: https://docs.unity3d.com/2021.3/Documentation/ScriptReference/Object.Instantiate.html
There were many examples on this page with instantiating projectiles so this helped a lot.

**PROBLEM:**
I applied one of the examples (the Rigidbody example) to the projectile script, however, It caused the bullets to constantly spawn every frame due to the Instantiate function happening in the update method.

**SOLUTION:**
I created an if statement and 2 float variables to check the fire rate and the time since the last fire. This would only instantiate a bullet after an interval of time.
































### TASK TWO- AREA COUNTDOWN

**PROBLEM:**
I had created a countdown timer by using TMPro and made it subtract by using time.deltaTime when it was more than 0. However, I did not know how to convert the float variable of the countdown to a string. 

**SOLUTION:**
I found a website that showed how to display the float as a string and also only display certain units in the number: https://gamedevbeginner.com/how-to-make-countdown-timer-in-unity-minutes-seconds/#convert_to_text 
I also asked my peer if there was an easier way to round the seconds and they showed me the use of string.Format("{0:n0}",timeCountDown)

![3rd](https://user-images.githubusercontent.com/114989045/199607209-f9b5c201-8b6e-4742-9d89-40ef04447cc0.png)



**PROBLEM:**
I created a cube, deleted its mesh, set the trigger on the box collider on and named it CountResetCollider. I then created an 'OnTriggerEnter' method to reset the timeCountDown float back to 60. The timer was not resetting when the player entered the cube collider.

**SOLUTION:**
The timer script was attached to the UI canvas from back when I was trying to make the timer work. I moved the script over to the player cube so that the ‘OnTriggerEnter’ method knew what needed to trigger the collider.


### TASK THREE- ENLARGE PLAYER PICKUP 

**PROBLEM:**
I created a pickup script so that when the player collides with the pickup object, the pickup disappears. When tested, the pickup would fall from the sky like desired, however, when it would collide with the plane, the plane collider triggered the collision and destroyed the pickup. 

**SOLUTION:**
I assigned the player object to the tag “Player” and used an if statement to compare tag and then destroyed when it is “Player”.

![4th](https://user-images.githubusercontent.com/114989045/199607257-7bbb2e14-a138-49e8-aeda-0e08e81c430c.png)



**PROBLEM:**
I created an if statement in the pickup script in the update function to countdown from 5 seconds. When the timer hit 0, it would shrink the player back to 1 in all axis, to its original size. However, this did not work as when the player would collide with the pickup, the pickup would destroy, therefore the pickup script would not countdown as it was attached to the pickup.

**SOLUTION:**
I asked a peer to help, and they showed me how to reference a script in another script. I used this to create a separate timer script and attached it to an empty game object called controller. This also meant moving the transforms for increasing and decreasing the player’s size to this script.

![5th](https://user-images.githubusercontent.com/114989045/199607298-910574e6-2aff-4897-90f4-ed332bc7cc8c.png)

![6th](https://user-images.githubusercontent.com/114989045/199607326-4c81e851-4d6a-4385-bd54-b8faa9215398.png)


### TASK FOUR- PRESSURE PLATES

**PROBLEM:**
I created a script to move a door open when a collision is triggered. I wanted the door to open and stay open using a force on the rigidbody of the door. I used GetComponent Rigidbody to access the door's rigidbody and then applied an upward force using AddRelativeForce. However, the door wound only jump open, and not stay open.

![Screenshot 2022-12-11 214123](https://user-images.githubusercontent.com/114989045/206930421-aa670582-29ae-4ebf-ba17-7ca27b7bc836.png)

**SOLUTION:**
I was using ForceMode.Impulse, when Ishould've been using ForceMode.Force as Impulse only applies the force for a small amount of time, where as Force applies it constantly. I also placed a cube near to where I wanted the door to stop opening as otherwise, the door would constantly lift up into the air. This acted as a door stop.

![Screenshot 2022-12-11 214202](https://user-images.githubusercontent.com/114989045/206930447-22cfdfad-25e8-4bbe-8e32-9dd8ffe83a9e.png)

**PROBLEM:**
I edited my scripts of moving the door using transforms to make a countdown. I wanted the countdown to start when the door is triggered to open and I want the door to shut back when the countdown reaches 0. I created a function called StartTimer and tested if it worked in Unity. I could see that the timer value was starting at the number i gave it (5) and then counting down the seconds when the door opens. It also shut the door when the timer reached 0. However, when the trigger is deactivated, and reactivated again, the door does not open again.


**SOLUTION:**
I realised that I had to reset the timer back to what it was set to. Therefore, I reassigned the variable timeRemaining which was countingdown back to its original given number. I put this into the if statement checking if the timer has run out just after the door moving to the close position.

![Screenshot 2022-12-11 220457](https://user-images.githubusercontent.com/114989045/206931599-30dbb06d-5460-4f07-9016-ac2131349d42.png)

### COMPONENT PACKAGE

**PROBLEM:**
I created a scene with 2 planes, a player object and a turret on the second plane. I wanted it so that when the player entered the second area, the turret would activate and start firing the bullets. I also wanted it so that when the player entered it, a timer would start and if the timer ran out, the turret would cool down for a set time and the cool down time would display.

To start, I created a PlayerMovement script, a TurretMovement script and a BulletController script. The TurretMovement script just updates the turret object to look at the player and the BulletController script instantiates the bullet prefab with a force repeatedly after a set time.

I wanted these scripts to be activated when the player collides with the second plane area collider.

I created a script called TurretOn which would find out when the player collides with the area, and pass a boolean value of true to both of the other scripts.


**SOLUTION:**
When trying to pass the boolean value from this TurretOn script to the other two scripts, I had set the boolean value to private, which meant the scripts could not access this value. I changed this to a public variable and used “ { get; private set} to make the variable accessible via scripts but not accessible in the Unity editor.

![Capture](https://user-images.githubusercontent.com/114989045/201912236-77443c27-1b4f-4ea1-840a-4996c37703a9.PNG)

**PROBLEM:**
I wanted the bullets fired to destroy after a set amount of time. I tried editing the update function in the BulletController script and thought creating a bulletTime float, decrementing it by time and setting that when this float is equal to 0, the clone gameobject of the instantiated bullet prefab would destroy by using clone.IsDestroyed. However, this did not work.

**SOLUTION:**
I asked a peer for some help. They showed me how creating a script for this destroy function would be the best way. I created a script called BulletDestroy and created an if statement to say that if bulletTime is less than or equal to 0, the gameobject that the script is on will destroy.

![Capture](https://user-images.githubusercontent.com/114989045/201926280-489aa458-71b4-4d19-bffb-aa389ec44922.PNG)

**PROBLEM:**
I wanted the turret to stop firing when the player has left the plane and plane area collider. So, I created an OnTriggerExit function and set the boolean variable turretOn to false. This did not work, as when the bullets were colliding with the area, it was setting turretOn as true due to the OnTriggerStay.

**SOLUTION:**
I created a tag called player and then created an if statement in both trigger functions to say if the collider tag is player, set the turretOn variable to true of false.

![Capture](https://user-images.githubusercontent.com/114989045/201932010-4c647517-ab73-48a9-bd85-f6e854218fac.PNG)

**PROBLEM:**
I wanted to make the amount of turrets accessed by the player editable. For example, if a user of the component package wanted to add or subtract turrets to the scene, the current amount of turrets will be accessed.

**SOLUTION:**
In the Timer script which is on the player object, I removed all of the variables referencing the TurretOn script for each turret and just created a list for all of them instead to count the amount of turrets.

![Capture](https://user-images.githubusercontent.com/114989045/204537096-07dbfab2-6368-4a89-8a45-c3a9d68bc33e.PNG)

In the Start function, I need to find the script to find out how many turrets are in the scene so I used "AddRange" to add those found and to find the turret objects, I used "FindObjectsOfType<TurretOn>()". This finds all the objects referencing the "TurretOn" script and adds them to the list on play.

![Capture](https://user-images.githubusercontent.com/114989045/204538748-841bf1a4-addd-4b91-8132-6cf81e32e7ff.PNG)

  
  


