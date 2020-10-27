# Shooting Enemy AI
This shows you how to create an enemy AI in unity which follow the player, retreat when the player player come near it and most importantly shoot projectile at the player. 
## 1. Making a new scene 
- Start this tutorial by creating a new scene in unity called 'Shooting Enemy AI' 
- Creating 2 square sprites, one is for the player and other is for the enemy. you do this by clciking on the Assets, create, sprite.
- After this change the colour of the player's sprite to blue and change the colour of the enemy's sprite to red. you do this by clicking on the sprite, then go to colour under the sprite render.
- Go to the player and under the Inspector window change the player's tag to 'Player' 
- Make a red circle in photoshop and import it into Unity. This circle will be used as the projectile of the enemy later on.
- Then make a folder called 'Prefabs' by right clicking in the Project window, then create, folder. After this put the red circle(the projectile), player and enemy sprites inside the folder.
- After that create a new folder called 'Scripts' by right clicking in the Project window, create, folder. Inside this folder create a script called 'Enemy'. 

## 2.The coding part
### Creating Variables
- In the script under the Public Class, create a public float called 'speed', we will be using this to adjust the speed of the enemy. After this, we will be creating a public float called 'StoppingDistance' this is used to make the enemy stay away from the player, which mean the higher this variable, the longer the distance between the enemy and the player will be. Then make another public float vatiable called 'retreatDistant' this is used to tell the enemy when they should move away from the player. Then create a public transform variable called 'player'. After this create a private float called 'TimeBtwShots' and then create a public float called 'startTimeBtwShots' these 2 variables are used to control how long does it take for the enemy to spawn a projectile. After this, make a public GameObject called 'projectile' which is used to store the enemy's projectile. the first part of the Script should look like this if it is done properply.

using System.Collections;
using System.Collections.Generic;
using System.Security.Cryptography;
using UnityEngine;

public class Enemy : MonoBehaviour
{

    public float speed;
    public float stoppingDistance;
    public float retreatDistance;

    private float timeBtwShots;
    public float startTimeBtwShots;

    public GameObject Projectile;
    private Transform player;
    
 ### Starting Function
 - In the starting function set the 'player' variable equal to the position of the game object that has the tag called 'Player' by using this line of code "player = GameObject.FindGameObjectWithTag("Player").transform;". Then set the 'timeBtwShots' equal to the 'startTimeBtwShots' this is a crutial part of the code, if you don't put this line of code here the enemy will shoot out the projectile in total of 60 times per second. if this is done correctly, it should look like this:
 
   void Start()
    {
    
        player = GameObject.FindGameObjectWithTag("Player").transform;

        timeBtwShots = startTimeBtwShots;
    }
 
 ### Update Function
 #### If statement
 - Inside the update function, create an if Statement and we will be using this if statement to check the distance between the player and the enemy. wee need to used this code "Vector2.Distance(transform.position, player.position)" to check the distance of the enemy and the player. also if the distance between these objects are larger than number of the 'stoppingDistance' variable then we want the enemy to move straight toward the player. Furthermore to make the enemy to move to the player, we need to set the enemy's current position euqal to the player's position. After this set the position of the enemy, the player,the speed of the enemy inside the brackets and times everything with Time.deltaTime to make sure that everything run smoothly "transform.position = Vector2.MoveTowards(transform.position, player.position, speed * Time.deltaTime);".
 



















