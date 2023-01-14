# TUTORIALS
## WEEK TWO-AREA COUNTDOWN

#### PLAYER CONTROLLER:

Create a player object and 2 planes.

Then, create a C# script called PlayerController and attach it to the player object.

In this PlayerController script, above the Start function, create a public float variable called speed. Creating this as public means that we can input and edit this value in the Unity editor.

In the Update function, create 2 local float variables called h and v. 

![Screenshot 2022-11-04 201036](https://user-images.githubusercontent.com/114989045/200065791-53ea03ba-88bf-4ca1-b717-a404b6985ffa.png)

As shown in the image above, these 2 variables are set as the inputs from the user. Input.GetAxis means that it needs 2 input values that are opposites. Horizontal gets the horizontal arrow keys (left and right) and vertical gets the vertical arrow keys (up and down).

Next, we need to use these input values and move the player object based on the float values. transform.Translate does this. By putting the variable h in the x co-ordinate and v in the z co-ordinate, this moves the player object in the direction of the floats inputted by the player.

This movement needs to have a speed so multiply these co-ordinates by the variable speed.

I have also put in a jump input shown below, however, you do not need this for this tutorial.

![Screenshot 2022-11-04 201102](https://user-images.githubusercontent.com/114989045/200065804-820af291-4bf4-46c4-be8b-e0d32bc192ef.png)


#### TIMER:

Create a C# script called Timer. Also attach this script to the player object.

At the top of the script, as shown above, type in using UnityEngine.UI; and using TMPro;. This lets us access the UI objects we are going to create.

Above the Start function, create 2 public variables. One that is a float called timeCountDown that is set to 60, and one that is a TextMeshProUGUI variable called countText. This set to nothing yet, therefore, we need to drag the UI TextMeshPro element that we want to refer to.

To do this, we first need to create this TextMeshPro object in the project. 

First, create a UI canvas and then in that canvas, create a TMP text object. Position this where ever you want your timer to appear on the screen.

![Screenshot 2022-11-04 203527](https://user-images.githubusercontent.com/114989045/200069399-180215af-f051-439c-8be7-c438f577c947.png)

The text in this TMP text object can be left as it is.

Next, drag this TMP object to the variable space where the Timer script is in the player object. This is our reference to that TMP object.

![Screenshot 2022-11-04 203942](https://user-images.githubusercontent.com/114989045/200070658-5fb387ce-37de-4f0d-a5ad-5dd9b25715c9.png)

Now that the UI is created, we need to make the timer count down from 60 seconds.

In the Update function, create an if statement to check if the variable timeCountDown is more than 0. If it is more than 0, then timeCountDown should decrement by Time, as shown below.

![Screenshot 2022-11-04 205009](https://user-images.githubusercontent.com/114989045/200072374-9655bec9-7b60-42e6-8232-07c538d2bec1.png)

We now need to convert this float value of timeCountDown to a string to then assign it to countText as countText will then display is in the TMP object.

This is done by the line string.Format("{0:n0}",timeCountDown). This gets the rounding value that we want to round the float by, and the float we are getting (timeCountDown).

Lastly, we want the timer to reset whenm entering a new area.

After the Start function, create a new function called OnTriggerEnter. In this function, set the variable timeCountDown as the value 60.

![Screenshot 2022-11-04 210212](https://user-images.githubusercontent.com/114989045/200074383-b0b2598d-37cb-4ba2-a357-6e699f424f99.png)


go back to the Unity editor and create a cube the size of the 2nd plane area. Place this above the plane and turn off the mesh renderer so that it is invisible. Click the IsTrigger box on this invisible object. This makes the box collider on this invisible object the collider referenced in the script.

![Screenshot 2022-11-04 210257](https://user-images.githubusercontent.com/114989045/200074307-b735e027-8a60-4f9d-9396-c3814f47d5a9.png)

This means that when the player object collides with this invisible object, the timer is reset back to 60 and counts down again.


