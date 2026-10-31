# Rock Paper Scissors
In this game you are playing against the computer. The computer selects its move based on your chosen difficulty level. Your win streak will be impacted by the result of each round and you will see the result, if it was a win, loss, or tie. 
 
## How to play 
1. Select Easy Mode or Hard Mode, depending on your perferred level of difficulty. If you select easy mode, playing paper, scissors, rock in that order allows you to win everytime. 
2. Click **Rock**, **Paper**, or **Scissors**.
3. The computer shows its move beside yours.
4. Rock beats scissors, scissors beats paper, and paper beats rock.
5. As you win, your win streak will update. If you lose, your win streak will reset to 0.

## How it works
The game contains 4 new main concepts: 
- If result was a win, loss, or tie for the player, it will state that instead of saying "someone won".
-  A win streak for the player, how many consecutive rounds the player has won, resets to 0 when the player loses.
- An easy and hard mode, gives control over difficulty, easy mode follows a repeating sequence, hard mode plays a random move. 
- The result text colour changing depending on the result, automatically updates to green for win, red for loose, and grey for tie. 

-** Win or loss**
When the game is first opened, the middle of the screen reads: "Let's Play Rock, Paper, Scissors! Can you beat the computer?" This is called the "result".
Under the function: winner, lines of code dictate the result based on the computer's move and the player's move. These lines of code feature an *if*, *else if, &&, and ==.  *
*If*: Used for inital check, if that line of code is true it will run. 
*Else if:* Used for secondary check, if the line above it was false, the following line will run. 
*&&*: Used to evaluate true or false playerMove and computerMove on a single line. If 2 ifs were used, this would create code that is harder to follow and maintain. 
*==*: Used when a value is eqaul to. If the player's move is equal to one of the three moves possible (rock, paper, or scissors) this code will run. 
If the line of code is true, the result text will display if the player won, lost, or if it was a tie. 

-** Win Streak**
In stored properties, currentWinStreak is a State var integers starting at 0 which will change. Int = 0 explains that the win streak is to represented with an interger and that it will always start at 0 when the game is first opened. An Int was chosen because we are counting with whole numbers. Under functions, "func updateStreak (won: Bool)" takes a boolean parameter true for win and false for loss. If won is true when a round is played, the game adds 1 to the curent win streak of the player. If won is false, the win streak is reset to 0. Each outcome in "winner" calls the updateStreak. UpdateStreak won adds one point to the streak, but updateStreak "!won" means it is false and the streak is reset to 0. 
In the body of the code, lines 110-113 dictate the colour, font, and font size of the win streak title in the game. The string allows for text to be displayed.

-** Easy and Hard Mode**
The state variables (@State var isHardMode) and (@State var easyModeStep) stores whether the game is in hard or easy mode. If isHardMode true, the game is set to hard mode and the moves are randomized. If hard mode false, it is in easy mode. The line also says " easyModeStep = 0" which guarantees the computer's first move will be rock, as the computer reads rock as 0. Rock being read as 0 allows the computer to constantly play the first move as rock, and counting by one each time to 1, then 2, then resetting to 0 so the computer alwasy plays the same series of moves on easy mode. 
Under functions, if hard mode is true, the computer will select a random number between 1-3. If the random number is 1, the computer plays rock. If the random number is not 1 but 2, the computer plays paper. If the random number is not 1 or 2 but 3, the computer scissors. 
If hard mode is false and easy mode is selected, the computer cycles through number 0, 1, and 2. 0 makes it generate rock, 1 make it generate paper, and 2 makes it generate scissors. The (easyModeStep +1) allows for the game to continously cycle through these numbers, increasing it by one each time. When it reaches 2, adding 1 makes 3, so 3 % 3 bring the number back to 0, allowing for easy mode to cycle. 
A Bool was chosen over a String for selection of hard mode because it only has two states, true or false, if hard mode was selected or not. 
%3 was selected over an if statement as it allows for one clean, short line of code. 

-** Result Text Colour**
*If: *Indicates if the following statement is true or false. 
*Result.contains*: 'Contains' is a built in function that every String has. It checks if the result of the game is true or false (win or lose). 
Arugment (ex. *"Win" *or *"Lost"*): The text you hand 'contains' as an argument explaing what to look for. 
*return colour.\_\_\_*: Explains what colour the result text will become if the statement is true. 
 
## What I added 
- The game now tells the player when they have won or lost. 
- The game shows the player's "Win streak", for how many times they have won using a function with a Boolean parameter.
- The game has an "Easy Mode" and "Hard Mode" options so they player can customize the difficulty when playing.
- The colour of the result text changes depending on result. When player wins, the text is green. When player looses, the text is red. When it is a tie, the text is grey. 
## Testing
| Test | Chosen Input | What should happen | Did happen |
| --- | --- | --- | --- |
|  Text change when I win |  Computer fixed at 1, I chose paper. | The result says who one won: "You win, paper covers rock!" |  I won. \*Note. I completed this in class on Friday, October 23 but did not commit it, hence why the change does not appear under the repositories. |
| Win Streak | Computer fixed at 1, I chose paper | After playing the game multiple times, result says who one won: "You win, paper covers rock!"|  After selecting paper multiple times, the win streak increased.  |
-** Test**: Win streak
**Chosen input: **computer fixed at 1, I chose paper then scissors. 
**What should happen: **I should gain a win streak of 1 then it should reset to 0. 
**What did happen:** I gained a win streak of 1 and then lost it.

-** Test:**** **Easy Mode** 
**Chosen input:** Continous sequence of computer playing rock, then paper, then scissors 
**What should happen:** After playing paper, scissors, rock I should win everytime. 
**What did happen: **I won everytime I selected paper, scissors, rock in that order. Win streak increased.

-** Test:** Hard Mode
**Chosen input:** Clicked hard mode then rock
**What should happen: **Computer generates a random move (1..3) 
**What did happen: **Random computer move was played, result was not consistent allowing for win streak to change. 

-** Test:** Win text result colour
**Chosen input: **Selected easy mode, player chooses paper, computer chooses rock. 
**What should happen:** Result text becomes green. 
**What did happen:** Result text became green. 

-** Test:** Loose text result colour
**Chosen input: **Selected easy mode, player chooses scissors, computer chooses rock. 
**What should happen:** Player looses, result text becomes red. 
**What did happen: **Play lost, result text became red. 

-** Test:** Tie text result colour
**Chosen input****: **Selected easy mode, player chooses rock, computer chooses rock. 
**What should happen: **Tie, result text becomes grey.
**What did happen:** Tie, result text became grey. 

-** Test: **Rock loses to Paper
**Chosen Input****: **Hard mode fixed at 2, I chose rock.
**What should happen:** Display text "You lost, paper covers rock!" and text colour becomes red.
**What did happen**: "You lost, paper covers rock!" was displayed and text colour was red.

-** Test: **Paper loses to Scissors
**Chosen Input****: **Hard mode fixed at 3, I chose paper.
**What should happen:** Display text "You lost, scissors cuts paper!" and text colour becomes red.
**What did happen**: "You lost, scissors cuts paper!" was displayed and text colour was red.

-** Test: **A tie in the middle of the streak.
**Chosen Input****: **Easy mode selected, played paper, scissors, then scissors again. 
**What should happen:** Display text "It's a tie"! and text colour becomes gray.
**What did happen**: "It's a tie!" was displayed and text colour was gray.

-** Test: **Easy mode comes round again.
**Chosen Input****: **I chose paper, scissors, rock, then paper.
**What should happen:** The computer goes through the (0..2) sequence then with the %3 returns to 0.
**What did happen**: Computer played rock on the fourth turn repeating the sequence. 

-** Test: **Back to easy mode after hard mode.
**Chosen Input****: **Clicked easy mode, choose paper, clicked hard mode, then easy mode, then clicked paper.
**What should happen:** Clicking easy mode resets easyModeStep to 0 so the computer's pattern starts from rock on the next play.
**What did happen**: The easy mode sequence reset after returing to easy mode, computer played rock. 


## Credits
 
- The starting game was written by Mr. Gordon.
- To create the game, Gemini AI was used. This platform helped me add the win streak, levels of difficulty to the game, and colour of result text.


