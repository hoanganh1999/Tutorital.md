# 2D Top Down Player Control in all diretion Tutorital
This tutorital shows how to make a simple 2D top player movement script. We can make this work by attaching a rigid body on to an object, and then in the script create a Vector2 variable called moveInput, this variable is used to detect the position of the character when we want to move. We can then make another Vector2 variable called moveVelocity to determine the velocity of the character. Also, set the moveVelocity equal to the moveInput varible times with speed. Before doing all of this, we must first set up a few things to start the project.

## 1. How to create a new scene

- Once the unity is opened, staring this by generating a scene called 'Movement Scene'

- Under the assets folder create a folder called 'Art/Sprites' by left clicking on the Assets then select create, folder. Then create a 2d sprite named 'Player' in the 'Art/Sprites' folder by going to the going to the top left of the unity and click on Sssets, then go to create, then go down and you will see Sprite, click on Sprite and make a square sprite and call it 'Player'.

- After that add a new rigid body 2D to the 'Player' by going to the player, add component, add rigid body 2D. After that go to the rigid body 2D and set the Body Type from dynamic to kinematic this is so that the player can only be affected by the user input. 

- lastly create a another folder called 'Scripts', inside the folder right click, create, C# script and name it "playController". once you have created the scipt double click on teh script to get it open on Visual Studio.


## 2.Coding

## Making Variables
- In the script, make a public flooat speed under 'public class' which used to handle how fast the player will move around the scene. After this make a private rigid body 2D called rb to handle the physic of the player. Then, create a private Vector2 called moveVelocity to determine the velocity of the player.  

using System.Collections;
using System.Collections.Generic;
using System.Runtime.CompilerServices;
using UnityEngine;

public class PlayController : MonoBehaviour
{
    
    public float speed;
    
    private Rigidbody2D rb;
    
    private Vector2 moveVelocity;




so that the player can only get affected by the control/user input but on the other hand does't get affected by the external force or the gravity.

