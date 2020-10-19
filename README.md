# 2D Top Down Player Control Tutorital
This tutorital shows how to make a simple 2D top player movement script. We can make this work by attaching a rigid body on to an object, and then in the script create a Vector2 variable called moveInput, this variable is used to detect the position of the character when we want to move. We can then make another Vector2 variable called moveVelocity to determine the velocity of the character. Also, set the moveVelocity equal to the moveInput varible times with speed. Before doing all of this, we must first set up a few things to start the project.

## 1. How to create a new scene

- Once the unity is opened, staring this by generating a scene called 'movement scene'

- Then create a 2d sprite named 'player/character'  
