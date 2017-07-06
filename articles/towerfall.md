# title
towerfall

# name
Towerfall on an FPGA

# roles
- hardware designer
- software engineer
- technical artist

# languages
- C
- SystemVerilog
- Swift

# tools
- Quartus
- Pixelmator
- Xcode

# subtitle
Video available [here](https://youtu.be/2JgICgRZdoE).

# article
I recreated a simplified version of the popular archery combat game Towerfall Ascension on a FPGA. I wrote hardware modules to manage the display and keyboard input, and programmed the game itself from scratch. 

## Software
On the software side, the game was programmed in C entirely from scratch. It interfaces with the display driver by communicating the id number, position, and dimension of each sprite over PIO blocks. 

The game code consists of [XXX] major components: input processing, physics, and collision detection. Each system is relatively simple, but together they create a game that feels quite similar to TowerFall. 

`Manually assembled sprite sheet
Collision system
Image file conversion with Swift script`


## Hardware
The FPGA used was an Altera DE2-115. 

### Design Choices

Since single-keyboard multiplayer can result in up to eight simutaneous key presses, I had to develop a PS/2 keyboard driver rather than use USB which can only read two simultaneous key presses. Additionally, PS/2 input made for a simpler 

We used a PS2 keyboard instead of a USB keyboard for input, and we did so because our game is two-player, with each player potentially inputting up to 4 inputs at once. A USB keyboard is simply not able to handle eight simultaneous inputs, and as an added bonus the PS/2 interface allowed us to run our game at a higher frequency than USB polling would allow. We used the provided PS/2 files—as well as a custom module, a key concatenator—to read key codes from hardware, which we forwarded to software using a PIO block.

Our project makes use of a sprite sheet containing every sprite used by the game. We store this sprite sheet in a 1-port ROM IP block. The VGA controller and color mapper display the game objects and environment by drawing to the screen using data from a frame buffer. The frame buffer is a 2-port RAM IP block, and is written to by a blitter during the VGA’s vertical blanking interval.

The software portion of the project primarily consists of the game.c file, which controls game state, game logic, and sprite drawing data. It sends the sprite drawing data to the blitter using nine sets of five PIO blocks. These sets of PIO blocks consist a 32-bit port for sprite address and 16-bit port for x position, y position, width, and height. The game state and game logic is controlled by a very complex and somewhat delicate mass of variables and conditional statements. Game programming is hard.