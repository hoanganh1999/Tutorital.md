# 2D Enemy Follow AI
This tutorial shows you how to create an enemy in unity which follow the player's character in a 2D space. This works by having the enemy tagging the player so whenever the player move the enemy will chase after the player. 
## 1. Creating a new scene

- Start this by creating a new scene in new call 'Enemy Follow Scene'.
- then create a folder called 'Art' under the project window. 
- Then add 2 square sprites one called 'Player' and other called 'Enemy'.
- Then change the colour of the 'Player' sprite to blue by clicking on the sprite, the go to Sprite Renderer then click on colour. Do the same thing with 'Enemy' sprite but change its colour to red.
- finally make a folder under the project windown called 'Scripts' by right click in assets windown, create, folder. after that, in the 'Scripts' folder create 2 scripts, one is called 'EnemyFollow' and the other one is called 'PlayerController'.

## 2. The coding part 
### Note since this tutorial is all about 2d Enemy Follow AI, so I am just going to talk brieftly about the Player's movement Script. 
- first add a Rigidbody 2D to the player then change the Body Type of the Rigidbody 2D from dynamic to kinematic.
- Add the 'PlayerController' to the player then change the speed of the player to 10

using System.Collections;
using System.Collections.Generic;
using System.Runtime.CompilerServices;

using UnityEngine;

public class PlayController : MonoBehaviour
{
  
    public float speed;
   
    private Rigidbody2D rb;
   
    private Vector2 moveVelocity;


    // Start is called before the first frame update
    void Start()
    {
      
        rb = GetComponent<Rigidbody2D>();
    }

    // Update is called once per frame
    void Update()
    {
        //this means that whenever the player presses the left arrow key or the down arrow key, the horizontal and vertical input is equal to -1(position of the player along the hoorizontal and vertical axis will be -1, this will make the player move to the left or down).
        //also whenever the player presses the right around key or the up arrow key, the horizontal input is equal to 1(position of the player in the horizontal axis and vertical will be +1, this will make the player move to the right or up).

        Vector2 moveInput = new Vector2(Input.GetAxis("Horizontal"), Input.GetAxisRaw("Vertical"));
        //set the movevelocity equal to speed x with speed, note is the code was left as "moveVelocity = moveInput * speed" the player would move faster when moves diagonally (solving it by putting normalized)
        moveVelocity = moveInput.normalized * speed;
    }
    void FixedUpdate()
    {
        //this is to adjust the the physic 
        //the player position adds with movevelocity(values) and times everything by time.deltatime
        rb.MovePosition(rb.position + moveVelocity * Time.deltaTime);
    }
}
