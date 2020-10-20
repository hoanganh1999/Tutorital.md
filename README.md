# 2D Top Down Player Control in all diretion Tutorital
This tutorital shows how to make a simple 2D top player movement script. We can make this work by attaching a rigidbody 2D on to an object, and then in the script create a Vector2 variable called 'moveInput', this variable is used to detect the position of the character when we want to move. We can then make another Vector2 variable called 'moveVelocity' to determine the velocity of the character. Also, set the 'moveVelocity' equal to the 'moveInput' varible times with speed. Before doing all of this, we must first set up a few things to start the project.

## 1. How to create a new scene

- Once the unity is opened, staring this by generating a scene called 'Movement Scene'

- Under the assets folder create a folder called 'Art/Sprites' by left clicking on the Assets then select create, folder. Then create a 2d sprite named 'Player' in the 'Art/Sprites' folder by going to the going to the top left of the unity and click on Sssets, then go to create, then go down and you will see Sprite, click on Sprite and make a square sprite and call it 'Player'.

- After that add a new rigidbody 2D to the 'Player' by going to the player, add component, add rigidbody 2D. After that go to the rigidbody 2D and set the Body Type from dynamic to kinematic this is so that the player can only be affected by the user input. 

- lastly create a another folder called 'Scripts', inside the folder right click, create, C# script and name it "playController". once you have created the scipt double click on teh script to get it open on Visual Studio.


## 2.Coding

## Making Variables
- In the script, make a public flooat called 'speed' under 'public class' which used to handle how fast the player will move around the scene. After this make a private rigidbody 2D called 'rb' to handle the physic of the player. Then, create a private Vector2 called 'moveVelocity' to determine the velocity of the player.  

using System.Collections;
  
using System.Collections.Generic;
  
using System.Runtime.CompilerServices;
  
using UnityEngine;

public class PlayController : MonoBehaviour
{
    
    public float speed;
    
    private Rigidbody2D rb;
    
    private Vector2 moveVelocity;

## Start Method
- Next in the start method we need to say 'rb' variable is equal to the rigidbody 2D that is already attached to the player, the Body Type of the Rigidbody 2D is already changed from from dynamic to kinematic. this means the player can only get affected by the control/user input but however the player won't be affected by the any external force or the gravity.

    void Start()
    {
        
        
        rb = GetComponent<Rigidbody2D>();
    }

## Update Method
- At the start the update method, create a Vector2 variable called Input, this variable is used to detect where we want to move. Set the Vector2 variable called moveInput equal to a new Vector2 inside the bracket set the x value equal to Input.GetAxis horizontal. this means that whenever the player presses the right around key, the horizontal and input is equal to +1(position of the player in the horizontal axis will be +1, this will make the player move to the right). whenever the player presses the left around key the horizontal input is equal to -1 which mean the player will move to the left. Also, pressing the up arrow will give the move input vector a Y value of 1 and pressing the down button will give the move input vector a Y value of -1. 

In additional, set the Vector 2 called 'moveVelocity' equal to the 'moveInput' Variable multiply with the speed 'variable' put '.normalized' after the 'moveInput' to stop the player from moving faster diagonally. 

void Update()
    {
        
        Vector2 moveInput = new Vector2(Input.GetAxis("Horizontal"), Input.GetAxisRaw("Vertical"));
        
        moveVelocity = moveInput.normalized * speed;
    }

## FixedUpdate Method
-All the script above is only for gathering player's input and to use this input to move the character in the environment by putting rb in the FixedUpdate Method and call the built in MovePosition funtion. Inside the bracket, state the current position of the player and add 'moveVelocity' to this position and time everything by Time.deltaTime. this is to make sure that the game run smoothly as long as the player hold down the arrow key. 

 void FixedUpdate()
    {
        
        rb.MovePosition(rb.position + moveVelocity * Time.deltaTime);
    }
}

## Combining everthing together
- Add the scipt to the player
- Test the character's movement by pressing any arrow key.
