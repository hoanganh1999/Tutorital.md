# 2D Enemy Follow AI
This tutorial shows you how to create an enemy in unity which follow the player's character in a 2D space. This works by having the enemy tagging the player so whenever the player move the enemy will chase after the player. 
## 1. Creating a new scene

- Start this by creating a new scene in new call 'Enemy Follow Scene'.
- then create a folder called 'Art' under the project window. 
- Then add 2 square sprites one called 'Player' and other called 'Enemy'.
- Then change the colour of the 'Player' sprite to blue by clicking on the sprite, the go to Sprite Renderer then click on colour. Do the same thing with 'Enemy' sprite but change its colour to red.
- Go to the 'Player' sprite and under the Inspector window click on Tag and change it to player 
- finally make a folder under the project windown called 'Scripts' by right click in assets windown, create, folder. after that, in the 'Scripts' folder create 2 scripts, one is called 'EnemyFollow' and the other one is called 'PlayerController'.

### Note since this tutorial is all about 2D Enemy Follow AI, so I am just going to talk brieftly about the Player's movement Script. 
- First add a Rigidbody 2D to the player then change the Body Type of the Rigidbody 2D from dynamic to kinematic.
- Add the 'PlayerController' scipt to the player then change the speed of the player to 10.

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
        Vector2 moveInput = new Vector2(Input.GetAxis("Horizontal"), Input.GetAxisRaw("Vertical"));
        moveVelocity = moveInput.normalized * speed;
    }
    void FixedUpdate()
    {
        rb.MovePosition(rb.position + moveVelocity * Time.deltaTime);
    }
}

## The Coding part for the 2D Enemy AI Follow
### Creating variables
- In the Script, under the public class make a public float called 'speed' this is used to control how fast does the enemy follow after the player in the scenne. Then create a private transform called 'target' this vatiable is used to hold the obkect that the enemy is supposed to run after. after this create a public float called 'stoppingDistance' this this used to stop the enemy from coming to too close to the player.

using System.Collections;

using System.Collections.Generic;

using UnityEngine;

public class EnemyFollow : MonoBehaviour
{

    public float speed;

    public float stoppingDistance; 

    private Transform target;

## Start Method
- At the start of the start method, we have to make the 'target' variable equal to the gameobject that has a tag called player and the transform information of the object. This will allow the enemy to find the gameobject that has a tag called player. 

void Start()
    {
    
         target = GameObject.FindGameObjectWithTag("Player").GetComponent<Transform>(); 
    }

## Update Method
-  In the update write transform.position this represents what position that you want the enemy to move. then set transform.position equal to Vector2.MoveTowards then inside the bracket say where you want the enemy to move from, to and at what speed. This is used to move the enemy character from his current position towards the target position(the player) at a fixed speed. Time.detltaTime is used to make sure that everything run smoothly. 

- Add an if statement to inside the bracket we will check the distance of the enemy and its target which is the player. if that distance is greater than the 'stoppingDistance' variable then the enemy can continue to move toward the player and if the distance is smaller the ling of code to tell the enymy to move toward the player won't run which stops the enemy from moving toward the player.

 void Update()
 
    {
        if (Vector2.Distance(transform.position, target.position) > stoppingDistance)
        {
            transform.position = Vector2.MoveTowards(transform.position, target.position, speed * Time.deltaTime);
        }
    }




