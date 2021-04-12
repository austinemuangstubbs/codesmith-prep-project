
//============Updated Code=============//

//Blackjack Game
//High Level Requirements:
//#1 A deck that doesn't repeat cards when drawn 


//#2 A user that draws cards
  //could be multiplayer or single player


//#3 Win or lose conditions


//There will be a house function plus user functions


//Create a deck array
  //drawing a card could be done with .pop() method
  //52 elements long
  //each element is a card. and '1 - Hearts' is what an element looks like. element would be string
  

 
 //Each persons hand is an array


//Game Starts
//Round starts
  //deck declared
function blackJackGame() {
  const fullDeck = [['2 of Spades', 2], ['3 of Spades', 3], ['4 of Spades', 4], ['5 of Spades', 5], ['6 of Spades', 6], ['7 of Spades', 7], ['8 of Spades', 8], ['9 of Spades', 9], ['10 of Spades', 10], ['J of Spades', 10], ['Q of Spades', 10], ['K of Spades', 10], ['A of Spades', 11], ['2 of Hearts', 2], ['3 of Hearts', 3], ['4 of Hearts', 4], ['5 of Hearts', 5], ['6 of Hearts', 6], ['7 of Hearts', 7], ['8 of Hearts', 8], ['9 of Hearts', 9], ['10 of Hearts', 10], ['J of Hearts', 10], ['Q of Hearts', 10], ['K of Hearts', 10], ['A of Hearts', 11], ['2 of Diamonds', 2], ['3 of Diamonds', 3], ['4 of Diamonds', 4], ['5 of Diamonds', 5], ['6 of Diamonds', 6], ['7 of Diamonds', 7], ['8 of Diamonds', 8], ['9 of Diamonds', 9], ['10 of Diamonds', 10], ['J of Diamonds', 10], ['Q of Diamonds', 10], ['K of Diamonds', 10], ['A of Diamonds', 11], ['2 of Clubs', 2], ['3 of Clubs', 3], ['4 of Clubs', 4], ['5 of Clubs', 5], ['6 of Clubs', 6], ['7 of Clubs', 7], ['8 of Clubs', 8], ['9 of Clubs', 9], ['10 of Clubs', 10], ['J of Clubs', 10], ['Q of Clubs', 10], ['K of Clubs', 10], ['A of Clubs', 11]]
  //deck shuffled
  const shuffledDeck = fullDeck.sort(() => Math.random() - 0.5)


  //all global variables declared at start

  let userHand = []
  let houseHand = []
  let draw
  let userCount
  let houseCount
  let turnCounter = 0
  let gameStillGoing = true
  let playAgainCounter = 0 
  
  //function that gets that total of a hand that is passed in
  function getHandTotal(handArray){
    let number = 0
    for (let i=0;i<handArray.length;i++){
      number += handArray[i][1]
    }
    return number
  }

  //how card's are taken from the deck and placed into hands
 
  function drawCard(handArray){
    draw = shuffledDeck.pop()
    handArray.push(draw)
  }

  function burnCard(deckArray){
    deckArray.pop()
  }


  //function that gives the user the ability to play multiple times without re-running code
  function playAgain(){
    if (playAgainCounter === 0) {
    console.log("Wanna play again, son?")
    } 
    playAgainCounter++;
    let playAgainChoice = ("Type 'yes' or type 'no'")
    if (playAgainChoice === 'yes') {
      console.clear()
      blackJackGame()
    } 
    if (playAgainChoice === 'no') {
      console.clear()
      console.log('Fine then. You ain\'t got no money anyway.')
    } 
    if (playAgainChoice !== 'yes' && playAgainChoice !== 'no'){
      console.log('You didn\'t follow directions, try again...')
      playAgain()
    }
  }

  //function that defines how user can interact with the game
  function userTurn(hand,handTotal){
    if (gameStillGoing === false){
      console.log('Game Over!')
      playAgain()
    }
    if(handTotal>21){
      console.log("You bust! Get outta here boiii")
      gameStillGoing = false
      playAgain()
  } else if (handTotal===21) {
      console.log("Black Jack!!!")
      gameStillGoing = false
      playAgain()
  } else {
      console.log('Would you like to hit or stay?')
      let choice = ("Type 'hit' or type 'stay'")
      if (choice === 'hit'){
        drawCard(hand)
        console.log('You have: ', hand)
        userCount = getHandTotal(userHand)
        userTurn(hand,userCount)
      }
      if (choice === 'stay'){
        houseTurn(houseHand,houseCount)
      } else if (gameStillGoing === true){
        console.log('You didn\'t follow directions, try again...')
        userTurn(hand,userCount)
      }
    }
  }

  //function that defines house logic
  function houseTurn(hand,handTotal){
    if (handTotal>21){
      console.log('The house is showing: ', hand)
      console.log('House busts! You win!')
      gameStillGoing = false
      playAgain()
    }
    if (handTotal===21){
      console.log('House stays. Reveal cards!')
      console.log('The house is showing: ', hand)
      console.log('House wins! Go home homie...')
      gameStillGoing = false
      playAgain()
    }
    if (handTotal<17){
      console.log('House hits...')
      drawCard(houseHand)
      houseCount = getHandTotal(houseHand)
      houseTurn(houseHand, houseCount)
    }
    if (handTotal >= 17 && handTotal<21){
      console.log('House stays. Reveal cards!')
      userCount = getHandTotal(userHand)
      houseCount = getHandTotal(houseHand)
      console.log('You have: ', userHand)
      console.log('The house is showing: ', houseHand)
      if (userCount > houseCount){
        console.log('You have a higher hand, you win!')
        gameStillGoing = false
        playAgain()
      } else if(userCount===houseCount){
          console.log('It\'s a standoff!')
          gameStillGoing = false
          playAgain()
      } else {
          console.log('House has a higher hand, you lose. Go home...')
          gameStillGoing = false
          playAgain()
      }
    }
  }

//Begin game by dealing cards to house and user
  //1st Cards
 
 let startButton = document.getElementById('play');
    startButton.onclick = function startGame() {
        alert('Welcome to BlackJack.  Let\'s play!');
    }
    
  console.log('')
  drawCard(userHand)
  drawCard(houseHand)


  //2nd Cards
console.log('Here are your first two cards.');
  drawCard(userHand)
  console.log('')
 console.log('You have: ', userHand)
  drawCard(houseHand)
  console.log('The house is showing: [ Hidden Card ]', houseHand[0])
  console.log('')
  //check house hand
  houseCount = getHandTotal(houseHand)
  //check user hand
  userCount = getHandTotal(userHand)
  //check if house got blackjack after first hand is dealt
  if(houseCount === 21 && (userCount!==21)){
    console.log('House wins with naturals and you ain\'t nobody.')
    gameStillGoing = false
    playAgain()
  }
  if(houseCount === 21 && userCount===21){
    console.log('You and House have 21! It\'s a standoff!')
    gameStillGoing = false
    playAgain()
  }
  //ask user hit or stay
  
  userTurn(userHand,userCount)

  
}
//first time invoking the game function
blackJackGame()  
