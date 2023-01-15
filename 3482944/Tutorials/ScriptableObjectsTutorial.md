# Scriptable Objects Tutorial

This will show how to make Scriptable Objects that can be used in future projects and tutorials.

This is done from the Brackeys video, so we will be following along with his steps of creating a card for Hearthstone.
https://www.youtube.com/watch?v=aPXvoWVabPY

## 1. Creating our Card Blank

Firstly you will need to create a card blank to act as our scriptable object I used the hearthstone card blank from 
https://www.deviantart.com/demaretc/art/Neutral-Epic-Monster-Empty-Card-507712903

![alt text](https://images-wixmp-ed30a86b8c4ca887773594c2.wixmp.com/f/82021352-fa8f-4e22-96a1-630256cab82e/d8ea1s7-bed07082-3953-480f-85d9-b5a3c37e9c1b.png?token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1cm46YXBwOjdlMGQxODg5ODIyNjQzNzNhNWYwZDQxNWVhMGQyNmUwIiwiaXNzIjoidXJuOmFwcDo3ZTBkMTg4OTgyMjY0MzczYTVmMGQ0MTVlYTBkMjZlMCIsIm9iaiI6W1t7InBhdGgiOiJcL2ZcLzgyMDIxMzUyLWZhOGYtNGUyMi05NmExLTYzMDI1NmNhYjgyZVwvZDhlYTFzNy1iZWQwNzA4Mi0zOTUzLTQ4MGYtODVkOS1iNWEzYzM3ZTljMWIucG5nIn1dXSwiYXVkIjpbInVybjpzZXJ2aWNlOmZpbGUuZG93bmxvYWQiXX0.a0KDGVm_dwfxMdFwGJXh9DvkjndPDGSbzEBFE2m0vQ4)

Make sure you get an image that does not have the values for Mana, Attack or Health, as we will add these in Unity.

In your main scene in Unity create a UI Canvas, and as a child to that canvas create a UI Image and add your card as the sprite, making sure to click Preserve Aspect.

Now create five seperate UI Text Objects as a child to the canvas called, Name, Descrption, Mana, Attack and Health.

Here if you want, you can change your text to be the same as the Hearthstone card text, I didn't to make it more clear to see where the text it.

Finally, create a UI Image that is above the Card Template in the Hierarchy so that your card looks like the below.
![alt text](https://i.imgur.com/9zk8kA4.png)

![alt text](https://i.imgur.com/00aGNLv.png)



## 2. Creating our Script

Now, in our project folder, create a scripts folder and create a C# script with the name `Card`
In that script we need to tell the script what data it will need for each card, so input the following code.

```.cs
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Card : ScriptableObject;
{
    public new string name;
    public string description;


    public Sprite artwork;

    public int manaCost;
    public int attack;
    public int health;

}
```
Making sure to change the MonoBehaviour to ScriptableObject, above ScriptableObject, add the code
```[CreateAssetMenu(fileName = "New Card", menuName = "Card")]```

This means that we can use the script from the asset menu, and it will create a new object in the menu called new card.

Now when you right click in your project menu and move to create, you should see Card at the top, click it and it could create an asset called "New Card".

## 3. Creating a card

Having created a new card from the menu, in the inspector you will be able to set its name, description, health, attack and mana cost.

For my image and references I have used the Annoy-o-tron card and my data looks as follows.
![alt text](https://i.imgur.com/OiqTzk7.png)

This will of course not do anything to the actual card yet, so to display them, we will create a new script called `CardDisplay` and attach it to our Card UI Object.

In the script add a public variable that is `public Card card;`

This will let you take the card you created and drop it into the script like so

![alt text](https://i.imgur.com/ZHVoUbc.png)

## 4. Adding our elements to our card

Within your CardDisplay Script add to the top `using UnityEngine.UI;` this will allow us to reference the UI within the Unity Engine in our Script.

Add the variables:

`public Text nameText`

`public Text descText`

`public Text manaText` 

`public Text attackText`

`public Text healthText`

`public Image artworkImage`

Back in Unity take the corresponding card elements and add them into the CardDisplay variables, like so:

![alt text](https://i.imgur.com/UV2NeLk.png)

Within the script now in the `Start` method we can add the following script to display the correct information on the card:

`nameText.text = card.name;` 

`descText.text = card.description;`


`manaText.text = card.manaCost.ToString();`

`healthText.text = card.health.ToString();`

`attackText.text = card.attack.ToString();`


`artworkImage.sprite = card.artwork;`

Now when you play in Unity, you should see that your card is updated, with all the correct information!

## Scriptable Object Complete.





