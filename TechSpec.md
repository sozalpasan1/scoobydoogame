## **Technology Stack**

### #1 PlayCanvas - https://playcanvas.com/

PlayCanvas looks pretty simple and has Graphical User Interface (GUI) editing for the core behaviors. 

Pros: In-browser editing, cross-platform support/mobile optimized, and has ways to support all the features this game HAS to have. Additionally, it has really nice lighting and shader elements that will make the Scooby Doo game look good. The physics engine will also make the running and capturing of treats more realistic. It is also open source on GitHub, and the learning curve isn't too bad. The main scripting language is JavaScript.

Cons: It requires an account and an internet connection to work, as it's a cloud-based editor. Its asset library is also not that large, so some assets may need to be imported. 

### Contenders : Babylon, Three.js, Pixi.js, Construct

- Babylon is trying to do way too many things and support far too much technology.  It can handle the Scooby Doo game, however it is designed to do EVERYTHING including VR and a million other things.  Its menus are far too complex to navigate and even the intro tutorials look way too niche for the amount of options it has avilable.
- Three.js is a library, not a game engine, so it won't actually help create a game. It is open-source, but the renders aren't even that clean, so it's not worth it.
- Pixi.js is all HTML 5 too lightweight and gives too much control. It doesn't have much of a learning curve and supports only the very core mechanics of game design. Every design should probably use this due to its feature customizability.
- Construct is a really clean 2D game engine with some 3D elements that are easy to use, but its 3D capabilities aren't enough for this game.

## **Architecture**

### 1. **ScoobyDooGame**

Manages game states, monster behavior, and player objectives.

- **Variables**
    - `snacksRemaining: int` - Number of snacks left for Scooby-Doo to eat.
    - `timer: int` - Countdown timer set to 30 seconds.
    - `isGameOver: boolean` - Indicates if the game has ended.
    - `scooby: ScoobyDoo` - Instance of Scooby-Doo character.
    - `monster: Monster` - Instance of the monster chasing Scooby.
    - `map: Map` - Represents the current 3D map.
- **Methods**
    - **`initializeGame`**
        - **Behavior**: Sets initial timer, snack count, and spawns Scooby, monster, and snacks on the map.
    - **`startLevel`**
        - **Behavior**: Loads a 3D map, places Scooby, and initializes monster behavior.
    - **`endLevel`**
        - **Behavior**: Ends level if Scooby finds Shaggy, is caught by the monster, or time runs out.
    - **`resetTimer`**
        - **Behavior**: Resets `timer` to 30 seconds when Scooby eats a snack.
    - **`checkGameOver`**
        - **Output**: `boolean` - Returns if the game has ended.
    - **`updateGameStatus`**
        - **Behavior**: Manages the countdown and win/loss conditions.
    - **`selectMap`**
        - **Behavior**: Selects a `Map` based on player clicks.

### 2. **Map**

Handles the layout, placement of snacks, and obstacles in the 3D environment.

- **Variables**
    - `layout: 3D Array` - Defines the map's structure and location of snacks and obstacles.
    - `snacks: List<Point>` - Positions of all snacks.
    - `shaggyLocation: Point` - Location of Shaggy on the map.
- **Methods**
    - **`loadMap`**
        - **Behavior**: Sets up the map's layout, placing snacks and obstacles randomly.
    - **`checkCollision`**
        - **Input**: `Point position` - Checks if a location has an obstacle.
        - **Output**: `boolean` - Returns true if an obstacle is present.
    - **`removeSnack`**
        - **Input**: `Point position` - Removes a snack if Scooby reaches the position.
        - **Behavior**: Updates `snacksRemaining` and resets `timer` in `ScoobyDooGame`.

### 3. **ScoobyDoo**

Represents Scooby-Doo, with movement and interactions within the map.

- **Variables**
    - `position: Point` - Scooby's current position.
    - `direction: String` - Current movement direction.
    - `speed: int` - Movement speed of Scooby.
- **Methods**
    - **`move`**
        - **Input**: `String direction`
        - **Behavior**: Moves Scooby based on direction, checks for snacks, and avoids obstacles.
    - **`resetPosition`**
        - **Behavior**: Sets Scooby's starting position when restarting or starting a new level.

### 4. **Monster**

Represents the monster that chases Scooby, with AI-driven path-solving movement and sound effects.

- **Variables**
    - `position: Point` - Current position of the monster.
    - `direction: String` - Direction the monster moves.
    - `soundRange: int` - Distance at which Scooby hears monster's sound.
- **Methods**
    - **`move`**
        - **Behavior**: Moves along the closest path to Scooby using `determinePath`. If Scooby is within `soundRange`, volume increases.
    - **`determinePath`**
        - **Behavior**: Determines shortest path from monster position to Scooby's position. 
    - **`resetPosition`**
        - **Behavior**: Places monster back at starting point after Scooby escapes or if game restarts.
    - **`checkCollisionWithScooby`**
        - **Input**: `ScoobyDoo scooby`
        - **Output**: `boolean` - Returns true if monster catches Scooby.
