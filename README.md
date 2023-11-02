# GRL-Movement_Flow

Movement in video games is a essential part when it comes to enjoying a game, especially while playing 3D Jump'n Runs. But what defines good movement and how can we make it feel good?


Based on Steve Swink's book [Game Feel](http://www.game-feel.com/), a [GDC talk](https://www.youtube.com/watch?v=hG9SzQxaCm8&t=461s) about designing a jump and [Game Maker's Toolkit](https://www.youtube.com/watch?v=yorTG9at90g&t=152s) analysis video about Celeste, we explore which parameters define the movement of a game.

Therefore we designed our own 3D Jump'n Run called Boss'n Run.

## Boss'n Run

### Original
Boss'n Run was originally my first video game I created with Simon Keller and Florian Gresser.
Our idea was to fuse a 3D Jump'n Run game with more complex fighting mechanics and challenging boss fights. 
(Hence the name!)

### Current Version

For this work I focused on exploring Game Flow in context of Boss'n Run, especially the Jump'n Run part.
Therefore I teamed up with Marc Mußmann who created a obstacle generator based on different movement parameter presets inside Unreal Engine 5 using the Altermesh plugin.

Below some screenshots for the look of this prototype:

The intro screen:
![Intro Screen](images/IntroScreen.png)
The level select screen: 
I defined different movement parameter presets imitating the movement feel of the N64 games: Super Mario 64, Donkey Kong 64 and Banjo Kazooie
We compared them to our own preset Boss'n Run.
For more information scroll down to evaluation section. 
![Level Screen](images/LevelScreen.png)
Now some Level screenshots:
![Level](images/LevelGeneration.png)
![level2](images/Stiernacke.png)
![level3](images/Done.png)


## Boss'n Run's Movement

In Boss'n Run it is possible to:
- walk
- run
- jump
- double jump
- triple jump
- long jump
- wall jump
- climb
- fast climb

![Options](images/mechanics.png)

In the follwing these movement options are briefly explained:

### Walk
This is the most basic movement option all most all games support. It consists of 3 variables:
- velocity (v) in meter per second ($m/s$), the speed in which the character traverses the game 
- accerleration (acc) in meter per $seconds^2$ ($m/s^2$) to acclerate the character to its max velocity
- deceleration (dec) in meter per $seconds^2$ ($m/s^2$) to decelerate the character back to zero velocity

We looked at how long the player character takes (time (t) in seconds ($s$)) to reach his max v from zero v, as well as how long it takes to stop from max v to zero v. As well as the distance (d) he needed to cover for that.

### Run
Same as walk, just that v, acc and dec have typically higher values so the player character traverses the game faster.

### Jump
The most essential movement mechanic in 3D Jump'n Runs. It consists of 2 variables:
- gravity in in meter per $seconds^2$ ($m/s^2$), typically negative to make the player character fall back down again.
- jump velocity (jump_v) in meter per second ($m/s$), an upward velocity to challenge briefly the gravitation force.

Here we looked at how high the character can jump (in meters), as well as how long he is in the air (in seconds), and which distance (in meters) we could cover while jumping with full speed.

### Doulbe Jump
A variation of the default jump, where only the jump_v is higher.

### Triple Jump
Another variation of the default jump, where the jump_v is at its highest.

### Long Jump
Also a variation of the default jump, where the jump_v is lower, but the character is moving with sprint velocity instead of move velocity (meaning the distance he covers is higher).

### Wall Jump
A special variation of the default jump. It is triggered when the character is already in the air and touching a wall, so he can jump of the wall with not only a upward velocity but also a sidewar velocity -> adding to the jump the variable:
- side jump velocity (wall_jump_v_h) in meter per second ($m/s$).

### Climb
Climbing is similiar to walking, but instead of performed at the ground it is performed at the wall.

### Fast Climb
Basically sprinting while climbing.

## Plots
We plotted 3 different aspects:
- the velocity over time and distance while accelerating from zero velocity to max velocity
- the overall movement over time and distance, meaning there is a acceleration part, a part where the character moves at constant max velocity and a deceleration part.
- the jump height over time and distance, meaning we look over the whole duration of the jump, how high and far the player characer goes.

### Boss'n Run Movement plots

Some example plots to showcase the walk movement over time and distance:

![Movement](images/WalkMov.png)

And the Jump over time and distance:

![Jumps](images/DJump.png)

## Evaluation

As already mentioned, I compared different movement parameter presets (in particular Super Mario 64, Donkey Kong 64, Banjoo Kazooie and our own Boss'n Run).
Therefore we let 14 participants play the different presets in generated levels:
![Evaluation](images/Eval.png)

For more information and explanation of these results please have a look in the report (a .pdf in the report folder) in this repository.
Or play the prototype yourself on [Itchio](https://brandnerkasper.itch.io/bossn-run)!
