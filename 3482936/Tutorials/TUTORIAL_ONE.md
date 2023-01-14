# TUTORIALS
## WEEK ONE-TURRET

#### PLAYER CONTROLLER:

Create a player object, a plane and a turret object in a 3D project in Unity.


create a C# script, name it PlayerController and attach it to the player object.


Above the Start function, create a public float variable called speed. Making this public means that we can adjust the value in Unity.


In the update function, create an if statement with the pass value set as the Left Arrow key input being pressed. 

![Capture](https://user-images.githubusercontent.com/114989045/199609092-3643ffb9-29d1-40cb-af4e-1e3c186ae5a7.PNG)

As shown in the image above, Input.GetKey is getting the player's key press input. KeyCode is defining which key on the keyboard.

In this if statement, the player object needs to be moved when the key is pressed. Therefore, transform.Translate will be used here. Translate moves the object that the script is attached to in the direction given in the co-ordinates. As it is the left key pressed, the player needs to move in the negative direction of the x-axis. this is done by putting -speed in the x co-ordinate.

To get the rest of the input movements, copy this statement and change the key input to the desire key. Also, change the axis of what speed should be applied.

![Capture2](https://user-images.githubusercontent.com/114989045/199610392-4099e7da-c434-4d86-985b-a4369bae9227.PNG)


#### TURRET CONTROLLER:

Create a C# script called TurretMovement and attach it to the turret object.

above the Start function, create a public Transform variable called target. This Transform variable finds the positon of the selected object. By making this variable public, we can assign the target as the player object. Therefore, this finds the positon of the player and assigns it to the variable named target.

In the update function, the turret needs to constantly look at the target. Therefore, transform.LookAt is perfect for this. 

![Capture3](https://user-images.githubusercontent.com/114989045/199612629-e219a604-0be4-4619-aee1-c52eb9df02fd.PNG)


#### BULLET CONTROLLER:

Create a 3D object for the turret barrel and a C# script called FireBullet. Attach the script to the turret barrel.

Also, create a 3D sphere object for the bullet and make it a prefab.

In the FireBullet script, create a public GameObject variable called bulletPrefab. We can assign the bullet prefab object in unity to the bulletPrefab variable as it is public.

Then, create three floats: two public called fireRate and bulletSpeed, and one private called timeSinceLastFire.

![Capture6](https://user-images.githubusercontent.com/114989045/199619051-86004b5b-a737-4928-ba38-731c2552bb94.PNG)


In the Update function, create an if statement asking if timeSinceLastFire is less than or equal to 0.

timeSinceLastFire is then set to the same value as fireRate. The value of fireRate can be inputted in the Unity editor.

We then want to make the bullet prefab appear from the turret. This is done by using Instantiate.

![Capture4](https://user-images.githubusercontent.com/114989045/199616350-32e1ea13-0a64-4a6b-8cd2-2ef39c593edc.PNG)

As shown in the image above, creating a local GameObject variable called clone and assigning it to the instatiation of the bullet prefab means that we can reference it later in the script. The instantiation finds the GameObject it needs to instantiate (bulletPrefab) in the given position (the position of the bulletPrefab) in the given rotation (the rotation of the bulletPrefab). 

The variable clone is now referenced to get the Rigidbody component of instantiated prefab. This is needed to then add a force to the Rigidbody. Using AddRelativeForce, we can send the bullet forward with velocity of the variable set bulletSpeed. ForceMode.Impulse makes the force immediate from the start.

Going back to the if statement, if the timeSinceLastFire is not less than or equal to 0, timeSinceLastFire is decremented by Time. This means that once timeSinceLastFire gets low enough again, it is less than or equal to 0 and can instatiate the bullet prefab.

![Capture5](https://user-images.githubusercontent.com/114989045/199619070-090cece3-5fc3-41da-953b-65047dd1eb5a.PNG)




