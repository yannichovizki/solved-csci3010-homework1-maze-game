Download Link: https://assignmentchef.com/product/solved-csci3010-homework1-maze-game
<br>



<strong>Objectives: </strong>

<ul>

 <li>Work with a multi-file c++ program</li>

 <li>Create a program that involves structs, classes, and enums</li>

 <li>Become (more) familiar with pointers and references</li>

 <li>Understand and review how objects are instantiated and how to use and manipulate them via methods and fields <strong>Turn In: </strong></li>

 <li>the individual files listed here: ​cpp, Maze.h, Maze.cpp, Player.h, Player.cpp,</li>

</ul>

Makefile

<ul>

 <li>You ​<em>may</em>​ split Board into its own ​h​ and ​Board.cpp​ files if you choose.</li>

</ul>

<strong>Instructions: </strong>

Your job is to implement a “maze” game. The word “maze” is in quotes here because “grid with random walls in it” is more accurate. As you’ll see from this description, in its most basic incarnation, this game can produce “mazes” that aren’t solvable—the player can’t move and the game will never end.

We’ll implement a basic, but forgiving text UI to play our game. You can think of this game as the first things that you would implement if you were trying to implement pacman. There is a single human player who you will ask which direction they want to go each turn, and the player will walk around collecting treasure until they reach the exit (or die).




Here are some screenshots of what our version looks like (see the last page for a complete run-through on a small board):

<table width="720">

 <tbody>

  <tr>

   <td width="360"> </td>

   <td width="360">Here, the player is the owl, walls are red crosses, treasures are pears, enemies are clown faces, and the exit is the green check mark. Each turn, the current player should be told which directions are legal moves. Every move that does not go off the board or run into a wall is a legal move. Diagonal moves are not legal moves. The current player will earn 100 points each time they collect a treasure. If an enemy moves onto a square with the human on it, the human is destroyed. If the human moves onto a square with an enemy on it, the human is destroyed. </td>

  </tr>

  <tr>

   <td width="360"> </td>

   <td width="360">If an enemy moves to a square with another enemy, neither player moves and the turn is forfeited. (Hint: think of this as the enemy “doing nothing”). The game ends when the player successfully reaches the exit or the enemies destroy the human.</td>

  </tr>

  <tr>

   <td width="360"> </td>

   <td width="360">Here is an example of an impossible board that was generated since the exit has no path to it from the player (you can’t move diagonally). The rules for board layout are as follows:–       The player always starts in the upper left corner–       The exit is always in the lower right corner–       Walls appear with a 20% chance in the spaces that are not the beginning space or the exit–       Treasures appear with a 10% chance in spaces that are not walls, the beginning space, or the exit–       You can decide where the enemies start, so long as they do not start on a wall or the exit.</td>

  </tr>

 </tbody>

</table>




<h1>Part 1 – Diagram your Program (due Tuesday, February 4th at 11:59pm)</h1>

We’ve provided you with the Makefile and headers for this homework. Your first goal is to plan out how they will interact. We’ve given you an example for the Player object here, so your job is to complete this for Board and Maze.




For each method of the given object, you should <em>briefly</em>​          ​ describe what it does (feel free to re-word our comments into your own words) and which other methods it will need to call. The main goal here is for you to think through the structure of your program before writing it. If you find when you are implementing it, that you need to change some decisions that you made here, that is fine.




Example: Player

<table width="720">

 <tbody>

  <tr>

   <td width="360">Player(const std::string name, const bool is_human)</td>

   <td width="360">initialize a Player with the given name and whether or not it is human</td>

  </tr>

  <tr>

   <td width="360">void ChangePoints(const int x)</td>

   <td width="360">update the points_ value according to the int passed in</td>

  </tr>

  <tr>

   <td width="360">void SetPosition(Position pos)</td>

   <td width="360">update the Player’s pos_ to the new position</td>

  </tr>

  <tr>

   <td width="360">std::string ToRelativePosition(Position other)</td>

   <td width="360">translate the other position into a direction relative to the Player by comparing other with pos_</td>

  </tr>

 </tbody>

</table>

<ul>

 <li>Note: none of the methods here rely on calling other methods—this is not the case for Board and Maze!</li>

</ul>







<h1>Part 2 – Implement your Program (due Friday, February 7th at 11:59pm)</h1>

<h2>Step 1 — the “basic” game (80 points)</h2>

We are providing header files and a Makefile. Your job is to implement the guts of the objects and re-create this game. Your display doesn’t need to exactly match ours (use your design and text UI skills as you wish), but the functionality should match ours.




The header files that we provide currently have most of the code commented out. This is so that you can uncomment and implement as you go. You ​<strong>should not attempt to implement everything before compiling</strong>​.




Here are two strategies that you might use when implementing this game:

<ul>

 <li>build your methods based on the workflow your working on. For example: if you’re working on building a board, you could work on writing the constructor and then overriding the &lt;&lt; operator so that you can print out the Board.</li>

 <li>start with ​Player​, test out the ​Player​ object, then move on to ​Board​, then ​Maze​. Again, <u>​testing as</u> <u>you go</u>​. Most of the functionality in ​Maze​ will depend on you having a working ​Board​.</li>

</ul>




In either case, you should not implement more than 1 function at a time before testing it out.




The ​TakeTurn​ function in ​Maze​ will likely be the last one that you implement, as it will depend on having all the other functions in place and working.




There are screenshots of an entire run-through of the game on the last page of this write-up.




Once you have finished implementing your game so that it works with a single human player, move on to adding enemies to your game.




Number of enemies: you may pick any number from 2 – 4. You do not need to let the user choose how many enemies are in the game. Your enemies should be implemented in such a way that adding another does not require you to add more code other than the initial set up of the additional enemy.




Note: we have used emoji to display our game, but this is not a requirement. Some systems and linux configurations do not nicely display emoji on the terminal. It is 100% acceptable to use regular ASCII characters to display your game!







<h2>Step 2 — improving the game (5 points)</h2>

The game we have described is not ​<em>super</em>​ fun, nor is it ​<em>entirely</em>​ functional—it’s possible (fairly likely even), that the player can’t even reach the exit. There is only one kind of treasure. There aren’t any traps. The enemies move via user input.




Once you have implemented the basic game, choose one of the following features to implement:

<ul>

 <li>Ensure that there is always an open path from the player to the exit. For example, you could just generate new boards until one has a path. You should not just generate a board with the edges free of walls or with no walls at all.</li>

 <li>Add different kinds of treasure. You should make the new kinds of treasure ​<strong>both</strong>​ have a different appearance from the basic treasure, and have a different point value. (add at least 2 new kinds of treasure)</li>

 <li>Add some danger to the board in the form of stationary traps. Make it possible for the player to lose lives and perish before exiting the board. These traps could be large, they could be invisible, they could be made of fire—it is up to you.</li>

 <li>Give the player a fixed amount of time or turns to complete the puzzle.</li>

</ul>




Make sure that you have included a comment in your main.cpp describing which of these 4 options you implemented!




<h2>General guidelines</h2>

The program that you turn in <strong>must compile.</strong>​ Even if your program is incomplete, ​ <strong>make sure it compiles</strong>​ .​ (You’ll get partial credit for a partially complete and compiling submission).

<strong> </strong>

Similarly, the code that you turn in <strong>must run</strong>​ . You will get credit for programs that are partially complete, but​ you will get a hefty deduction for programs that do not run. <strong>Make sure that it runs. </strong>​          There will be autograder​         tests on Gradescope to test compilation and some functionality of your work. In addition, we will be testing your code on the coding.csel.io and the vm.




<strong><u>10 points will go to style and comments</u></strong>. Your files and functions should have comments. We should know<u>​ </u> how to run your program and how to use your functions from your comments. Refer to the style guide on the course github to help you out here.




Your variables should have meaningful names. Your code should be easily readable. If you have complex sections of code, you should use inline comments to clarify. You should follow the style guidelines posted on our course github.




You should not have redundant code—you should use loops, conditionals, and helper functions to avoid copy+pasting code. If you find yourself copy+pasting lots of code—pause and think about your design. Refer to the example code and guidelines associated with lecture 5 (Jan 29/30) to help you here.




As a reference, our Maze.cpp about 350 lines, our Player.cpp is about 40 lines, and our main.cpp is 25 lines (all counts including whitespace and comments).

Happy coding and remember to post questions on piazza! If you’d like to see more examples of what happens in different situations, just let us know and we will provide more examples!

<h2>Step 3 — extra credit (up to 15 bonus points)</h2>

You cannot get points for extra credit unless you have completed both step 1 and step 2. We <strong>highly</strong>​         <strong> recommend</strong> choosing #1 as the feature that you implement for step 2 if you are doing the extra credit.​




Give the enemies strategies so they are computer controlled. If you have multiple enemies, they can all follow the same strategy or different strategies. Extra credit will be scaled on how sophisticated your enemy strategies are.




<table width="720">

 <tbody>

  <tr>

   <td width="360"> </td>

   <td width="360">The example to the left shows a complete run through of the game. The user’s choice is case insensitive. If they enter an invalid option, they are prompted again. Once the user steps onto a space with a treasure, that treasure should be collected — the user should have 100 more points and the treasure should disappear.                              </td>

  </tr>

  <tr>

   <td width="360"> </td>

   <td width="360"> The human player earns 1 point for successfully getting to the exit.   When the game ends, it should report how many points each player has.</td>

  </tr>

 </tbody>

</table>


