## **Technology Stack**

### PlayCanvas - https://playcanvas.com/

PlayCanvas looks pretty simple and has Graphical User Interface (GUI) editing for the core behaviors. 

Pros: In-browser editing, cross-platform support/mobile optimized, and has ways to support all the features this game HAS to have. Additionally, it has really nice lighting and shader elements that will make the Scooby Doo game look good. The physics engine will also make the running and capturing of treats more realistic. It is also open source on GitHub, and the learning curve isn't too bad. The main scripting language is JavaScript.

Cons: It requires an account and an internet connection to work, as it's a cloud-based editor. Its asset library is also not that large, so some assets may need to be imported. 

### Other Contenders : Babylon, Three.js, Pixi.js, Construct

- [Babylon](https://bablyonjs.io) is trying to do way too many things and supports far too much technology.  It can handle the Scooby Doo game, however it is designed to do EVERYTHING, including VR and more.  Its menus are far too complex to navigate and even the intro tutorials look way too niche for the amount of options it has avilable.
- [Three.js](https://threejs.org) is a library, not a game engine, so it won't actually help create a game. It is open-source, but the renders aren't even that clean, so it's not worth it.
- [Pixi.js](https://pixijs.com) is all HTML 5; it's too lightweight and gives too much control. It doesn't have much of a learning curve and supports only the very core mechanics of game design. However, it doesn't support 3D modeling well.
- [Construct](https://www.construct.net/en) is a really clean 2D game engine with some 3D elements that are easy to use, but its 3D capabilities aren't enough for this game.

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
        - **Output**: `boolean` - Returns `true` if the game has ended.
    - **`updateGameStatus`**
        - **Behavior**: Manages the countdown and win/loss conditions.
    - **`selectMap`**
        - **Behavior**: Selects a `Map` based on player clicks.

### 2. **Map**

Handles the layout, placement of snacks, and obstacles in the 3D environment.

- **Variables**
    - `obstacles: List<Point>` - Positions of all obstacles.
    - `snacks: List<Point>` - Positions of all snacks.
    - `shaggyLocation: Point` - Location of Shaggy on the map.
- **Methods**
    - **`loadMap`**
        - **Behavior**: Loads in the map's layout from the selected map and randomly places snacks and obstacles in it.
    - **`checkCollision`**
        - **Input**: `Point position` - Checks if a location has an obstacle.
        - **Output**: `boolean` - Returns true if an obstacle is present.
    - **`removeSnack`**
        - **Input**: `Point position` - Removes a snack if Scooby reaches the position.
        - **Behavior**: Updates `snacksRemaining` and resets `timer` in `ScoobyDooGame` if they are at the same position.

### 3. **ScoobyDoo**

Represents Scooby-Doo, with movement and interactions within the map.

- **Variables**
    - `position: Point` - Scooby's current position.
    - `direction: String` - Current movement direction.
    - `speed: int` - Scoob's movement speed.
- **Methods**
    - **`move`**
        - **Input**: `String direction`
        - **Behavior**: Moves Scooby based on the direction.  Addionally, checks for snacks at the new location.
    - **`resetPosition`**
        - **Behavior**: Sets Scooby's starting position when restarting or starting a new level.
    - **`snackCheck`**
        - **Behavior**: Checks for snacks at the current position; returns true if one exists.

### 4. **Monster**

Represents the monster that chases Scooby, with AI-driven path-solving movement and sound effects.

- **Variables**
    - `position: Point` - Monster's current position.
    - `direction: String` - Current movement direction.
    - `soundRange: int` - Distance at which Scooby hears monster's sound.
    - `monsterRender: int` - Randomly selects an index that grabs a representation of a monster within the array of monsters.
- **Methods**
    - **`move`**
        - **Behavior**: Moves along the closest path to Scooby using `determinePath`. If Scooby is within `soundRange`, increases volume.
    - **`determinePath`**
        - **Behavior**: Determines shortest path from monster position to Scooby's position. 
    - **`resetPosition`**
        - **Behavior**: Places monster back at starting point after Scooby escapes or if game restarts.
    - **`checkCollision`**
        - **Input**: `Point position`
        - **Output**: `boolean` - Returns true if monster catches Scooby.

## **Figma**
[View the Figma design](https://www.figma.com/board/ly3BYcJqnPvnaGub5JjfAw/ScoobyDooGame?node-id=0-1&t=VOovutvVnNDUNEef-1)

