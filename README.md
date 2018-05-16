# Cornell Clue: A CS 3110 Final Project

## Interface
![screenshot](https://github.coecis.cornell.edu/szk4/cs3110-finalproject/blob/master/static/interface.png)

## About the Game
The beloved Mr. Touchdown was apparently the victim of foul play and was found in one of the rooms of his Cornell-themed home. The object of the game is to discover the answer to these three questions: 1st. Who? Which one of the several suspects did it? 2nd. Where? 3rd. With What Weapon?

The answer lies in the little envelope containing 3 cards. One card tells who did it- another card reveals the room in which it all happened, and the third card discloses the weapon used.

You, along with 5 other AI's, will try and bring Mr. Touchdown justice. By the process of deduction and good plain common sense, the first player to identify the 3 solution cards hidden in the little envelope, wins the game. During their turn, player's roll, guess, and finally, if they are in a room, they have an option to make a "Suggestion" about which person and weapon were used in that specific room in order to gain information. One by one, players must try and refute this information or skip sharing information if it does not contradict the user's guess.

Finally, a player can make a final "Accusation" and name a suspect, weapon, and character.
If they are right, then they win the game! Else they are declared a loser and the game continues
without them.

Some rules of "Cornell Clue" differ slightly from the original Clue. For more information about the game, one can click on the "Help" button during gameplay.

## How to Run
Before one can play the game, make sure that OCaml (v4.06.0) and Opam (v1.2.2) are installed.

The GUI is written using Js_of_ocaml, so run the following command:
`opam install js_of_ocaml js_of_ocaml-ocamlbuild js_of_ocaml-camlp4 js_of_ocaml-lwt`

In order to initialize the game, the player should open up to the folder of the
game in their command terminal and type `make gui` in order to start the game.

## Compiling and Running the Javascript
- to run all of the files + compile, enter: `make compile`
- to run the front-end, enter: `make gui`
- to run the test cases, enter `make test`

## Key Game Features
- Game: A custom “Clue” narrative  
- Customization: Selecting one's player and a difficulty of the game
- AI: Different difficulties enabling player's to move, guess, share and essentially "think" differently
- Graphics: A custom OCaml/Javascript GUI

## System Design
We have designed the following 6 modules in order to implement our project:

### [controller.ml(i)]:
- Sets up initial game state, with user’s choice of character and difficulty
- Controls and updates the game state based on player and AI moves
- Keeps track of all the specifics of game play: this includes but is not limited to players, player locations, current turn, turn order of users, cards, and win_combination of cards

### [player.ml(i)]:
- Keeps track of all of the player’s attributes, including their character, the three cards they were originally given, their location, as well as their notes/checklist of information
- Handles any moves taken by the player including moving locations, guesses, accusations, and using passage

### [enemy_ai.ml(i)]:
- Initializes enemy AI’s that play against the user as either easy, medium, or hard
- Uses custom record to holds data on specific AI’s characteristics such as character, cards, difficulty, checklist, etc.
- Has functions to simulate game play including roll, move, and guess, the latter two which are based on AI difficulty

### [main.ml]:
- Contains game engine
- Handles input from the users, including roll, moving location, guesses about the character, weapon, or room, evaluates them into new states, and outputs them into the Updates console

### [gui.ml(i)]:
- Holds the board information including but not limited to: rooms, character locations, etc.
- Updates display based on whether information is shared, player has won, etc.

### [types.ml(i)]:
- Contains all types needed across several files, such as characters, rooms, weapons, state, etc.
- Has functions that are needed universally such as next player functions, type conversion functions, etc.

## Work Distribution
- [Shirley](https://github.coecis.cornell.edu/szk4) implemented all of the front-end, including designing the GUI layout with the board and updates in [gui.ml(i)]. She also worked on connecting the front-end display and back-end to make a working REPL in [main.ml]. She also worked on game setup in [controller.ml(i)]. She worked an estimated 80 hours.

- [Alisha](https://github.coecis.cornell.edu/am2658) designed and set up the project files and structure of the game, implemented many of the locations functions in [main.ml(i)] which were used validated location buttons for the front-end, as well as separate AI algorithms for the different AI difficulties in [enemy_ai.ml(i)]. She also implemented several of the major functions in [controller.ml(i)] and [player.ml(i)]. In terms of design and front-end, she worked on the custom card designs in Illustrator. She worked an estimated 45 hours.

- [Mahfuza](https://github.coecis.cornell.edu/mms398) implemented some of the enemy AI functionality in [enemy_ai.ml(i)]. She also worked organizing the code, such as compiling them into [types.ml(i)]. She wrote most of the specifications included in the .mli finals. She also worked on most of the test cases in [test.ml] and the accompanying debugging. She worked an estimated 35 hours.

- [Katy](https://github.coecis.cornell.edu/kev29) implemented [controller.ml(i)], [enemy_ai.ml(i)], and [player.ml(i)] and the action sequences. Additionally, she designed the enemy_ai design with probability shifts and calculated algorithm for the AI players. She also designed the con_to_gui, gui_to_con game loop with mutual recursion, and worked with Shirley to connect front-end to back-end in [main.ml(i)].  She worked an estimated 45 hours.

## External Dependencies
Js_of_ocaml allowed us to make a GUI in Ocaml, but compile and display is using JavaScript in a web browser. We use Js_of_ocaml in [gui.ml(i)] and [main.ml] to display our custom Clue board.

## Acknowledgements
Most of the graphics were our own, but we used a printable clue board from eagle-time.com. We also referenced [Legend Of Zolda](https://github.com/mindylou/legend-of-zolda) a CS 3110 Fall 2017 for more information on how to set up Js_of_ocaml.
