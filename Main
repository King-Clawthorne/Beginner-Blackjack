import random

currentCards = {}
dealersCards = {}

values = (("1", 1), ("2", 2), ("3", 3), ("4", 4), ("5", 5), ("6", 6), ("7", 7),
          ("8", 8), ("9", 9), ("10", 10), ("Jack", 10), ("Queen", 10),
          ("King", 10), ("Ace", (1, 11)))


def GetStartingCards():
  card1 = values[random.randint(0, len(values) - 1)]
  card2 = values[random.randint(0, len(values) - 1)]

  cardTable = {card1, card2}

  return cardTable


def GetAceValue(currentScore, isDealer=False):
  if not isDealer:
    while True:
      aceInput = input(
        f"Your current score is {str(currentScore)} Would you like your ace to equal 1 or 11?\n"
      )
      if aceInput == "11" or aceInput == "1":
        return int(aceInput)
        break
      else:
        print('Please enter either "1" or "11"')
  else:
    if currentScore < 11:
      return 11
    else:
      return 1


def returnOneCard():
  card = values[random.randint(0, len(values) - 1)]

  return card


def main():
  busted = False
  currentCards = GetStartingCards()
  dealersCards = GetStartingCards()
  currentValue = 0
  dealerValue = 0
  hasAce = 0
  print("You currently have these cards in your hand:")
  for value in dealersCards:
    tempValue = 0
    if value[0] == "Ace":
      tempValue += GetAceValue(tempValue, True)
      dealerValue += tempValue
    else:
      dealerValue += value[1]
  for value in currentCards:
    print(value[0])
    if value[0] != "Ace":
      currentValue += value[1]
    else:
      hasAce = True
  if hasAce > 0:
    while hasAce > 0:
      aceValue = GetAceValue(currentValue)
      currentValue += aceValue
      hasAce -= 1
  print(f"Your total value is {currentValue}")

  while True:
    if currentValue < 21:
      nextMove = input(
        f'Your score is {currentValue} would you like to hit or stand?\n')
      if nextMove.lower() == "hit":
        card = returnOneCard()

        cardVal = card[1]
        cardName = card[0]

        currentValue += cardVal
        print("You got a " + cardName + "!")
        print(f"Your current score is {currentValue}")
      elif nextMove.lower() == "stand":
        print(f"Your current score is {currentValue}")
        break
    else:
      if currentValue > 21:
        busted = True
        print("You busted!")
      break
  if not busted:
    print("Dealers cards are:")

    for value in dealersCards:
      cardName = value[0]

      print(cardName)

    print(f"With a value of {dealerValue}")

    while dealerValue < 17:
      newCard = returnOneCard()
      cardName, CardValue = newCard[0], newCard[1]

      dealerValue += CardValue

      print(f"Dealer hit a {cardName} and now has a value of {dealerValue}")

    if dealerValue <= 21:
      if dealerValue < currentValue:
        print("You Won!")
      elif dealerValue == currentValue:
        print("It was a tie!")
      else:
        print("Dealer Won!")
    else:
      print("Dealer Busted!")

  print("End")


while True:
  main()
  playInput = input(
    "Press enter to play again! or say quit to stop the program\n")
  if playInput.lower() == "quit":
    break
