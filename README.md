# Big Brain Blitz
#### Video Demo: https://www.youtube.com/watch?v=GMi23kDUn38
## Introduction and Inspiration

My six-year-old daughter loves playing the game "MASTERMIND" with me, which was created by Israeli telecommunications expert Mordecai Meirowitz in 1930. [[1]](https://boardgamegeek.com/boardgamedesigner/1060/mordecai-meirowitz) I let her know as part of my final project I would create a game that is inspired by MASTERMIND, so that she could play it with me on her tablet. She was very excited to know that her dad was making a game just for her! 

From a practical standpoint, web UI development and design have been areas that I've wanted to improve upon for a long time. I found during the "Homepage" exercize I got very excited to learn more about bootstrap. I saw there were opportunities to leverage the framework to build slick interfaces in ways that I struggled to implement in the past while attempting to use raw HTML+CSS. My goal going into this project was to focus on creating a really clean, sleak and easy to use UI for the game.

My final project is at the intersection of these two interests.

## Technologies Used
1. HTML / CSS
2. JavaScript
3. JQuery
4. Bootstrap
5. Flask

## Code Overview

1. Bootstrap [[2]](https://getbootstrap.com/docs/5.3/getting-started/introduction/) was used as the main front-end technology. I was able to contain all of the UI structure for the game board and user-feedback mechanisms in the index.html file. My goal was to have the web-page render well both in Safari for OSX and iOS, so that my daughter could play it with me on her iPad or my iPhone. I choose to limit the number of "guess" rows to 11, even though the original game had 12, in order to maintain user accessibility. I felt that if the peg circles were too small and squishes, it would be hard to register clicks on a mobile device. 11 rows was a happy compromise. Each guess row has a corresponding "clue" row, that serves as the games feedback to the user on how close they are to solving the code. Each black peg represents a right color guess, in the right position. I created style.css in the static folder, and configured the routing to static so that I could use ginja's ability to load the resource using url_for.

2. JavaScript and JQuery [[3]](https://api.jquery.com) were used to code the UI interaction and logic. When the page loads for the first time a new random code is generated and the game board is intialized. The user then has the opportunity to submit their guesses using any combination of 4 pegs using 6 colors. Players can select which color they would like to place in each guess circle by tapping on the color to activate it, then tapping on a guess circle to fill it with that color. Once finished, the player then submits their guess. The logic then evaluates each code peg, if the code peg color matches to a guess peg color in the same column, then a black peg is awarded. If an exact match is not found in the same column, then the remaining pegs are checked, and if there is a color match in any of the guess pegs, then a white peg is awarded. If all four guess pegs match with the corresponding code peg in the same column, then the player wins the game. If not, the game continues in a new guess row. If the player submits their final guess and does not correctly determine the code, then they lose the game. I used the game rules defined on [[4]](magisterrex.files.wordpress.com) magisterrex.files.wordpress.com to build and validate the game logic.
   
3. Bootstrap modals were used to provide feedback to the user in several scenarios: a.) If the user has not selected all of the pegs with a color, the user will be prompted to make sure all four pegs are selected, b.) If the user wins the game, they will be asked if they would like to start a new game, yes or no, c.) If the user loses the game, they will be asked if they would like to start a new game, d.) I added a button to allow the user to manually reset the game if they wish to do so.
   
4. The scope of this project was to allow for local game play, but I choose to build it out using the Flask framework so that it could easily be scalable in the future by connecting to an API endpoint, and having a server determine the random code, and provide user feedback to the local client. bigbrainblitz.py, .flaskenv, routes.py, and \_\_init\_\_.py contain the flask server config. The game can be run on a local network using flask run --debug --port 8080 --host 0.0.0.0 while activated in the venv.

5. ChatGPT [[5]](http://chat.openai.com) was used to help build the logic to generate the random code, as well ask ask a few questions about optimal usage of the bootstrap UI functionality.

6. UAT (User Acceptance Testing) I demoed the proof of concept game for my daughter once the core functionality was built out. There was a feature request from her to add in the ability to "choose your own code." I thought this was a great idea, as when playing together it adds an element of excitement for her, being able to try to find a code that "daddy can never solve!"

## References / Resources

[1] - https://boardgamegeek.com/boardgamedesigner/1060/mordecai-meirowitz \
[2] - https://getbootstrap.com/docs/5.3/getting-started/introduction/ \
[3] - https://api.jquery.com \
[4] - https://magisterrex.files.wordpress.com/2014/07/mastermindrules.pdf \
[5] - http://chat.openai.com