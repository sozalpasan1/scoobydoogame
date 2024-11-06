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
        - **Behavior**: Ends level if Scooby finds Shaggy or if caught by the monster.
    - **`resetTimer`**
        - **Behavior**: Resets `timer` to 30 seconds when Scooby eats a snack.
    - **`checkGameOver`**
        - **Output**: `boolean` - Returns if the game has ended.
    - **`updateGameStatus`**
        - **Behavior**: Manages the countdown and win/loss conditions.

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

Represents the monster that chases Scooby, with AI-driven movement and sound effects.

- **Variables**
    - `position: Point` - Current position of the monster.
    - `direction: String` - Direction the monster moves.
    - `soundRange: int` - Distance at which Scooby hears monster's sound.
- **Methods**
    - **`move`**
        - **Behavior**: Adjusts movement based on Scooby's position. If Scooby is within `soundRange`, volume increases.
    - **`resetPosition`**
        - **Behavior**: Places monster back at starting point after Scooby escapes or if game restarts.
    - **`checkCollisionWithScooby`**
        - **Input**: `ScoobyDoo scooby`
        - **Output**: `boolean` - Returns true if monster catches Scooby.
