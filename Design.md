## **1\. Scooby-Doo Snack Simulator**

## **2\. Define the Purpose**

* **There are going to be multiple different 3D maps.**  
* **You are Scooby-Doo, and you need to eat up a certain amount of Snacks before a monster which is chasing you gets you**  
  * Imagine the brainrot backrooms videos, where you’re in a map and you have to run away from the monster, but this time Scooby-Doo (you) is trying to eat all the hidden snacks across the map. There will be music emanating from the monster, and as it gets closer to you it gets louder. 
  * While Scooby is running around, there will be a timer counting down from 30 seconds. If Scooby eats a snack, the timer resets to 30 seconds. The end goal is that Scooby finds Shaggy, and frees him. That’s how you win. You have to avoid the monster while eating snacks and looking for Shaggy.  
  * There will be a timer display at the top of the screen.
  * Monster should be one of these guys

!["image"](https://github.com/MiloMessinger/Sean-scoobydoogame/blob/main/image1.png?raw=true)

* **Identify the Target Audience**  
  * People who like Scooby-Doo and pretty much anyone tapped into video games can play this. It’s supposed to be a scary game but not really. 

## **3\. Conceptualize the Design**

### **Aesthetics (Look)**

* **Visual Style**  
  * HauntedHouse-esque theme, darker colors “spooky vibe”  
    * Gothic architecture, lighting should be relatively dim, things should have exaggerated shadows and sharp strong lines, not smooth soft lines. There can be light sources across the map, like chandeliers, lanterns, or lamps. 
    
  * **Color Scheme**  
    * See images below  
    * Dark, murky feel 
  * **Typography**  
    * [https://www.fontspace.com/category/spooky](https://www.fontspace.com/category/spooky)  
    * Anything that's readable from there  
      * I liked “FREAK OUT” by graphicsauceco  
  * **Layout**  
    * [https://youtube.com/shorts/pqUWnTyib9c?si=TRzndKCEO2ANC5\_U](https://youtube.com/shorts/pqUWnTyib9c?si=TRzndKCEO2ANC5_U)  
      * The final game will basically be this but reskinned \+ the snack and shaggy elements.  
      * This should give a good idea of the “skeleton” of the game  
      * Kanye (the monster) is chasing you (Scooby-Doo). As the monster gets closer the music gets louder. While you are running from the monster, a 30 second timer is counting down and you need to eat a “snack” that's randomly placed on the map to reset the timer. While you are eating snacks and running away from the monster, you are looking for shaggy. 

      Shaggy is going to be placed in a random room across the map. Scooby has to find him. Ideally, when the game is started, Shaggy's spawn point is as far as possible from Scooby. The reward for winning is a win screen.
      
    * Add decorations around the map. Gargoyles, bookshelves, long tables, chandeliers, big bedrooms, vanities, make it look like an old abandoned mansion. 
    
    These decorations can be scattered across the map, and Scooby can jump over them.

!["image"](https://github.com/MiloMessinger/Sean-scoobydoogame/blob/main/image2.png?raw=true)

!["image"](https://github.com/MiloMessinger/Sean-scoobydoogame/blob/main/image3.png?raw=true)

!["image"](https://github.com/MiloMessinger/Sean-scoobydoogame/blob/main/image4.png?raw=true)

!["image"](https://github.com/MiloMessinger/Sean-scoobydoogame/blob/main/image5.png?raw=true)

### **Functionality**

* **Core Features**  
  * “Eating” a snack basically means that you run on top of the floating snack and then the timer resets. 
  No bonuses for eating snacks. Just reset timer.

!["image"](https://github.com/MiloMessinger/Sean-scoobydoogame/blob/main/image6.png?raw=true)

Imagine the snack is like this, floating a little off the ground and glowing. The snack can be whatever you want, but it should be glowing a little bit and be hovering just off the ground.

All you have to do is run on top of it, then the snack should disappear.

* **User Flow**  
  * When the user clicks the “Play” button in the menu, they get spawned into a random location on the map. The monster is spawned after 10 seconds at the same spot the user is spawned, so the user better get moving. As mentioned before, the user needs to reset the timer by eating snacks. The game ends if the timer goes to 0 or if the monster touches the user. You win the game by finding Shaggy. So the entire game is spent eating snacks, running from the monster, and checking all areas of the map for Shaggy.  
* **Interactive Elements**  
  * When the user opens the game, there's a menu that has the Play Button and the settings button. Settings are for game settings, like Audio, video quality, control mapping.
  * The Play Button loads a new screen, where the user selects their map of choice. After choosing their map, they spawn at a random location on the map and the game commences  
  * Users use WASD to control Scooby’s movement. Jump used with the Space button. That's all the controls.
  * Keeping it simple allows for the user to dive straight into the action

### **4\. Create Design Sketches**

* **Wireframes**  
  * !["image"](https://github.com/MiloMessinger/Sean-scoobydoogame/blob/main/image7.png?raw=true) 
  * I ran out of creations but this is roughly what it should look like. The settings cog should be in the top right corner, and there shouldn't be those weird buttons on the far left and right. It should just be the Play and settings button.  
  * !["image"](https://github.com/MiloMessinger/Sean-scoobydoogame/blob/main/image8.png?raw=true) 
  * Map select could look something like this, but retaining the same spooky theme.
  * Maps have the general shape of a maze.