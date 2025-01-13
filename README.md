# Space Gold Rush Games
This is the documentation for the game "Space Gold Rush" created in Code.org's sprite lab. The link to the project is found [here](https://studio.code.org/projects/spritelab/JiRXjBa3ueQIiQPIPyr2fxkPC_ymE5n2Jz2RPtxYHb4/edit).

**Game Objectives:**
* Collect as many coins as you can
* Avoid the UFO
* Change the difficulty to increase the speed of all moving objects; the coins and the UFO
* Player speed will remain the same regardless of the difficulty mode chosen

## Code Documentation

### Starting the Game
1. The background is set to the space background which stays throughout the game.
2. The difficulty mode buttons are then created, put in place, and set to a reasonable size.
3. The title screen is shown. It reads "Space Gold Rush" with the subtitle being "Choose Difficulty"

![alt text](D46FA77E-D005-4134-9DFA-748220C8D35E.png)

### Controls

**W and Up buttons:** Move up\
**S and Down buttons:** Move down\
**A and Left buttons:** Move left\
**D and Right buttons:** Move right

![alt text](image-2.png)
![alt text](image-3.png)

**Explanation:** I used event blocks to make the player character (the orange alien) move by a certain amount of pixels. I represented this by assigning a variable called `movement` which is set to 10, meaning that the player will move by 10 pixels in a certain direction while any of the arrow keys are clicked. However, if the player is touching the edges, it will not be able to move further in that direction due to the "edges stop ____ from moving" block.

### Difficulty Modes

There are 3 event blocks that recognize when one of the difficulty mode buttons are clicked and sets the enemy UFO and coin speeds accordingly. The main variable to take note of that is located under these event blocks is the `otherSpeed` variable. This variable represents the speed for both the coins and UFO. I could have chosen to separate the speeds of the coins and the UFO but then thought that having the coins move at higher speeds with increasing difficulty was reasonable. This also meant that both objects could use the same function to control their movements. Here are the enemy UFO and coin speeds for each of difficulty:\
**Easy/Ez mode:** `otherSpeed` is set to 10.\
**Medium/Mid mode:** `otherSpeed` is set to 13.\
**Hard/AHH! mode:** `otherSpeed` is set to 16.

![alt text](image-5.png)

### `runGame()` Function
This function is run regardless of the difficulty mode the player chooses. It is responsible for running the game after the player chooses one of the difficulty modes. This function is called when one of the difficulty buttons are clicked.
#### Steps
1. A sound plays in response to the button being clicked.
2. Title screen is hidden.
3. All the difficulty mode buttons disappear.
4. The variable `Coins` is initialized and set to 0. This variable is the "score" for this game.
5. The variable `movement`, as mentioned earlier, is initialized and set to 10. This variable controls the movement speed for the player character,
6. The variable `Coins` is shown in the top-left corner of the screen throughout the game,
7. The player sprite is created on the right side of the screen, its size is set, and it begins wobbling. Note that `wobble()` is a function already built into Code.org's Sprite Lab
8. 5 coin sprites are created, and they call the `hunt()` function, which causes them to wander the map at a speed designated by the `otherSpeed` variable mentioned earlier (the value of this variable depends on the difficulty mode. The higher the difficulty, the higher the value and speed). The `hunt()` was already built into Code.org's Sprite Lab as the `wandering()` function but I just modified it to include the otherSpeed variable.
9. The UFO sprite is created on the left side of the screen, opposite to the player alien sprite.
10. Like the coin sprites, the UFO also uses the `hunt()` function to wander the map. Like the coins, the UFO's speed is designated by the `otherSpeed` variable

![alt text](image-4.png)

### Collecting Coins
In the code below, an event block is used to run code when a coin sprite makes contact with the player sprite. When that happens, the code below the event are executed. This is what it does:\
1. A sound plays to indicate that a coin has been picked up by the player. It is a different sound from the one from the button clicks earlier.
2. The value of the `Coins` variable is increased by 1.
3. The coin sprite that touched the player sprite is removed.
4. In its place, a new coin sprite is created and placed in a random location. Its size is the same as the original. The new coin also begins using the `hunt()` function to wander the map just like the others.

![alt text](image-6.png)

### Player Collision with UFO
The code below uses another event block to execute code when the player sprite hits the UFO sprite. When that happens, the code below the event are executed. This is what it does:\
1. An explosion sound plays to indicate that the player has been terminated by the UFO.
2. A "Game Over" message is displayed in the form of a title screen block. In the place of a subtitle, the string "Coins Collected: " is concatenated with the variable `Coins` to display a message showing the reader their score after being hit by the UFO.
3. The game hides all the sprites; the player, the coins, and the UFO.
4. The `Coins` variable is hidden since it will be displayed to the player anyway via the message on the screen,
5. A new sprite is created for a restart button. Its size is set to 125 to make it more visible.

![alt text](image-7.png)

### Restarting the Game
An event block is used to execute code when the restart button sprite is clicked. This is what happens when it is clicked:\
1. Set `Coins` variable to 0, before starting a new game.
2. The restart button sprite is removed.
3. The same button click noise is used (previously used for the difficulty buttons).
4. The title screen is hidden (which showed the game over messages and the amount of coins collected after the UFO hit the player).
5. The `runGame()` function is run to start the game all over again.
Note that the difficulty cannot be adjusted once chosen, as the restart button immediately starts the game without showing the difficulty menu. This is intentional. To chamnge the difficulty mode of the game, you will need to restart it.

![alt text](image-8.png)