## P0 ##
- Point class/all position methods
    - Whole game is based on your location and the monster's relative to the map. Also checks for collisions with walls, shaggy, snacks and monster, allows death
- scooby: ScoobyDoo
    - is the playable character/protag of the whole game.
- monster: Monster
    - Only objective is to run from the monster. Need a monster
- startLevel: void
    - allows game to start
- initializeGame: void
    - initializes game
- direction: Monster
    - lets monster move in a direction; can chase scooby
- shaggy: not in a class but obviously needed
    - objective is to find shaggy so you need a shaggy
- all move/direction methods/vars
- speed: Scooby/Monster

## P1 ##
- checkCollision: Monster
    - checks if monster hits scooby
- isGameOver: ScoobyDooGame
    - game can end
- checkGameOver: ScoobyDooGame
    - game can end
- int timer: ScoobyDooGame
    - adds time mech to game
- updateGameStatus
- endLevel
- resetTimer
- all resetPosition
- determinePath
- snackCheck
- removeSnack
- snacks <list>

## P2 ##
- mapSelect
- monsterRender
- soundRange
- map class
- map
