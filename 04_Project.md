# Number Guessing Game

Guess a number from 1 to 100 and then check whether it's right with system generated number or not.
You have 10 attempts to do it.

## HTML Code goes here:
### Code:
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Project 4</title>
    <link rel="stylesheet" href="fun.css">
</head>
<body style="background-color: bisque;">
    <div class="heading">WELCOME TO PRITAM'S GAME</div>
    <div id="wrapper">
        <h1>Number Guessing Game</h1>
        <p class="design">Guess a random number between 1 and 100 <br> You have 10 attempts to guess the right number</p>
        <br>
        <form action="" class="form">
            <label for="guessField" id="guess">Guess a number</label>
            <br>
            <br> 
            <input type="text" class="guessField" id="guessField">
            <br>
            <input type="submit" value="Submit Guess" id="subt" class="guessSubmit">
        </form>

        <div class="resultParas">
            <p>Previous guesses: <span class="guesses"></span></p>
            <p>Guesses Remaining: <span class="lastResult">10</span></p>
            <p class="lowOrHi"></p>
        </div>
    </div>
</body>
<script src="fun.js"></script>
</html>
```

## CSS part goes here:
```css
body{
    text-align: center;
}
h1{
    background-color: yellow;
    padding: 10px;
    margin-left: 30%;
    margin-right: 25%;
    border-radius: 5px;
    border: 2px dashed blue;
}
.design{
    background-color: grey;
    padding: 7px;
    font-size: x-large;
    margin-left: 17%;
    margin-right: 17%;
    text-align: center;
}
#wrapper{
    border: 2px solid black;
    border-radius: 6px;
    background-color: whitesmoke;
    margin-left: 15%;
    margin-right: 15%;
    margin-top: 1%;
}
#guess{
    font-weight: bolder;
    font-size: larger;
}
.guessField{
    height: 20px;
    padding: 5px;
    border: 3px solid gainsboro;
    text-align: center;
    font-size: larger;
}
#subt{
    padding: 4px;
    font-weight: bold;
}
p{
    font-size: x-large;
}
.heading{
    font-family: 'Times New Roman', Times, serif;
    font-size: xx-large;
    font-weight: bolder;
    background-color: aqua;
    padding: 10px;
    border-radius: 5px;
    margin-left: 20%;
    margin-right: 20%;
}
#newGame{
    background-color: blue;
    padding: 5px;
    margin-left: 20%;
    margin-right: 20%;
}
```

## JS part goes here:
### Code:
```javascript
let randomNumber = parseInt(Math.random()*100 + 1)

const submit = document.querySelector('#subt')
const userInput = document.querySelector('#guessField')
const guessSlot = document.querySelector(".guesses")
const remaining = document.querySelector(".lastResult")
const lowOrHi = document.querySelector(".lowOrHi")
const startOver = document.querySelector(".resultParas")

const p = document.createElement('p')

let prevGuess = []      // This is the array which contain the guesses guessed by the user
let numGuess = 1        // This is the number of guesses the user has done [when the user reaches at guess no 10 then we will disable the submit button]

let playGame = true     // This is the flag value for starting the game [every game contains this type of flag value, game will not start without checking the flag values]

if(playGame){
    submit.addEventListener('click',function(e){
        e.preventDefault()

        let guess = parseInt(userInput.value)
        validateGuess(guess)
    })
}


function validateGuess(guess){
    // This function will check whether the user has given a valid number or not means number should be between 1 to 10
    if(isNaN(guess)){
        alert('Please enter a valid number')
    }else if(guess < 1){
        alert("Please enter a message more than 1")
    }else if(guess > 100){
        alert("Please enter a message less than 100")
    }else{
        prevGuess.push(guess)   //Pushing the guess in the array
        
        if(numGuess > 10){
            displayGuess(guess)
            displayMessage(`Game Over. Random number was ${randomNumber}`)
            endGame()
        }else{
            displayGuess(guess)
            checkGuess(guess)
        }
    }
}

function checkGuess(guess){
    // In this function the value is checked and displayed the message whether that is low or high
    if(guess === randomNumber){
        displayMessage(`Congo!! You guessed it right`)
        endGame()

        
    }else if(guess < randomNumber){
        displayMessage(`Guess is TOO low`)
    }else if(guess > randomNumber){
        displayMessage(`Guess is too high`)
    }
}

function displayGuess(guess){
    // This function will display the guess in the array and also cleans the textbox for inputting next guess
    userInput.value = ''    // After the value is accepted it field must be empty for taking next input
    guessSlot.innerHTML += `${guess},  `   // Adding the values in the array [focus on the sign '+=']
    numGuess++      // After this the number of guesses should be updated
    remaining.innerHTML = `${11 - numGuess}`
}

function displayMessage(message){
    // Displaying the message which has been created before but not declared there
    lowOrHi.innerHTML = `<h2>${message}</h2>`   // Everyone is providing message so we have to just print it
}

function endGame(){
    //
    userInput.value = ''
    userInput.setAttribute('disabled','')   // 'disabled' works in key-value pair so we have given a empty value after 'disabled'. It will disable the user to give inputs after 10 attempts
    p.classList.add('button')   // 'button' class will be added, by which we can able to press a button [this is the another method of creting button]
    p.innerHTML = `<h2 id="newGame">Start a new game</h2>`
    startOver.appendChild(p)
    playGame = false    // Necessary to stop the game
    newGame()
}

function newGame(){
    //
    const newGameButton = document.querySelector('#newGame')    // Selecting the button created in endGame() function
    newGameButton.addEventListener('click',function(e){
        randomNumber = parseInt(Math.random()*100 + 1)      // Creating another random number for new game
        prevGuess = []      // Clearing the previous array
        numGuess = 1        // Clearing the number of guesses for previous one
        guessSlot.innerHTML = ''    // Deleting the previous array from the screen
        remaining.innerHTML = `${11 - numGuess}`    // Calculating number of guesses left for this game
        userInput.removeAttribute('disabled')       // After guessing 10 times the user input was disabled so here we have remove the attribute named 'disabled'
        startOver.removeChild(p)    // The button for new game was displayed here so removing the entire child which is 'p' tag

        playGame = true     // Making the flag true again so the game can start again
    })
}

```