const suits = ["Hearts", "Spades", "Clubs", "Diamonds"]
const rank = ['Ace of ', '2 of ', '3 of ', '4 of ', '5 of ', '6 of ', '7 of ', '8 of ', '9 of ', '10 of ', 'Jack of ', 'Queen of ', 'King of ']
const cardValue = [11, 2, 3, 4, 5, 6, 7, 8, 9, 10, 10, 10, 10]
const deck = []
const playerCards = []
const computerCards = []

const playAgain = () => {
  deck.splice(0)
  for (let s = 0; s < suits.length; s++) {
    for (let r = 0; r < rank.length; r++) {
      deck.push({
        suit: suits[s],
        rank: rank[r],
        value: cardValue[r]
      })
    }
  }


  for (i = 0; i < deck.length; i++) {
    j = Math.floor(Math.random() * (i + 1))
    let temp = null
    temp = deck[i]
    deck[i] = deck[j]
    deck[j] = temp
  }
  console.log(deck)
  cardDealt = deck.pop()
  console.log(cardDealt); 
  playerCards.push(cardDealt)
  document.querySelector('.dealtCardOne').textContent = cardDealt.rank + cardDealt.suit;
  cardDealt = deck.pop()
  console.log(cardDealt); 
  playerCards.push(cardDealt)
  document.querySelector('.dealtCardTwo').textContent = cardDealt.rank + cardDealt.suit;
  cardDealt = deck.pop()
  console.log(cardDealt); 
  computerCards.push(cardDealt)
  document.querySelector('.dealtCardThree').textContent = cardDealt.rank + cardDealt.suit;
  cardDealt = deck.pop()
  console.log(cardDealt); 
  computerCards.push(cardDealt)
  document.querySelector('.dealtCardFour').textContent = cardDealt.rank + cardDealt.suit;
}

// const getPlayerCurrentTotal = () => {
// }
// console.log(total)
// }

const hitPlayer = () => {
  cardDealt = deck.pop()
  console.log(cardDealt); 
  const newLi = document.createElement('li')
  newLi.textContent = cardDealt.rank + cardDealt.suit
  document.querySelector('.playerCards').appendChild(newLi);
  playerCards.push(cardDealt)
  let total = 0
  for (let i = 0; i < playerCards.length; i++) {
    total += playerCards[i].value;
    if (total > 21) {
    
    document.querySelector(".winner").textContent = "House Wins!!!";
    document.querySelector('#playerTotal').textContent = total
  }
}
}

// document.querySelector('#playerTotal').textContent = getPlayerCurrentTotal()
document.querySelector('.play').addEventListener('click', playAgain)
document.querySelector('.hit').addEventListener('click', hitPlayer)