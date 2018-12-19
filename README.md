# Nim Game

**Nim** is a mathematical game of strategy in which two players take turns removing objects from distinct piles. The game will be played between the human player and the computer player. In this project, you will handle the computer player while a user plays the game. Choosing the optimal game strategy is complicated and will likely require you to do things that we have not covered yet. We will use a simplified version here.

**The rules** Given two piles, numbered 1 and 2, in which each pile contains some numbers of stones. In each turn, a player can choose only one pile and remove one, two, or three stones from that pile. The player who cannot move is considered to lose the game (The one who takes the last stone is the winner).

**Learning Objectives**
- integers (int)
- conditionals
- iteration
- input and output

-------------------

## Nim Game Introduction

> Nim is a mathematical game of strategy in which two players take turns removing objects from distinct heaps or piles. On each turn, a player must remove at least one object, and may remove any number of objects provided they all come from the same heap/pile. The goal of the game is to be the player who removes the last object. —— [Wikipedia](https://en.wikipedia.org/wiki/Nim)

### Project Description
* Initialize both piles to have 5 stones each.
* You will need a **while** loop to play the game (this will be in addition to the while loop in the code that is used to ask whether the human player wants to play another game.)
* Play alternates between the human and computer. Use a Boolean variable to keep track of who is playing. The human player starts.
* Within this **while** loop:
>When it is the human player’s turn:
>>1. First prompt for the pile (1 or 2). Continue prompting until valid pile number is entered. A valid pile is non-empty and numbered 1 or 2.
>>2. Next prompt for a number of stones to be removed from that pile. Continue prompting until a valid number of stones is entered.
>
>When it is the computer’s turn:
>>1. Select the pile that the human player did NOT use on their turn. If the selected pile is empty, select the other pile, i.e. the one the human player used on their turn (note that if both piles are empty the game should have already ended).
>>2. The number of stones to be removed by the computer is always 1 stone.
>
>Then, remove the stones from the pile. Display the number of stones in each pile after removal. Remember to switch players.
* The player who takes the last stone is the winner.
* When the game has come to its conclusion, the program should output whether the human or the computer won. It then should display the cumulative record and ask the user whether to play again. (And if the user selects to play again, your program should.)
* If the user choose not to play the game again, the program should display a goodbye message.
* Your program should verify that each of the user's moves is valid. (That is, the pile must be legal, the user must remove between 1 and 3 stones, and the user must not remove more stones than the pile holds.) If the user's move is illegal, your program should repeatedly print a sensible error message and get a new input, until the user selects a legal move.

### The Pic
![image](https://github.com/liutiantian233/Nim-Game/blob/master/While%20loop.png)

### The beginning of the code
```python
@TianTian
print("\nWelcome to the game of Nim! I'm probably going to win...")
print('''Nim is a simple two-player game based on removing stones.
         The game begins with two piles of stones, numbered 1 and 2. 
         Players alternate turns. Each turn, a player chooses to remove one, 
         two, or three stones from some single pile. The player who removes the
         last stone wins the game.''')

play_str=input("Would you like to play? (0=no, 1=yes) ")

human = int(0)     # Initialize the number of times humans win the game
computer = int(0)  # Initialize the number of times computer win the game
```
### The loop of the code
```python
@TianTian
while int(play_str) != 0:  # use while to determine if the game starts
    
    pile1 = int(5)
    pile2 = int(5)
    print("Start --> Pile 1:",pile1,"   Pile 2:",pile2)
    
    while (pile1 > 0) or (pile2 > 0):  # use while to determine if the pile is empty.
        pile = int(input("Choose a pile (1 or 2): "))
        
        while ((pile == 1)and(pile1 == 0))or((pile == 2)and(pile2 == 0)):
            # If one of the piles is empty. No more stones can be removed from this pile.
            
            print("Pile must be 1 or 2 and non-empty. Please try again.")
            pile = int(input("Choose a pile (1 or 2): "))
            
        else:
            
            while (pile != 1) and (pile != 2):
                # If the number of the pile is not legal. Can't continue.
                
                print("Pile must be 1 or 2 and non-empty. Please try again.")
                pile = int(input("Choose a pile (1 or 2): "))
                
            else:
                stones = int(input("Choose stones to remove from pile: "))
                
                while (stones > 3) or (stones < 1):
                    # If the number of the stones is not beween 1 and 3. Can't continue.
                    
                    print("Invalid number of stones. Please try again.")
                    stones = int(input("Choose stones to remove from pile: "))
                    
                else:
                    print("Player -> ",end='')
                    print("Remove",stones,"stones from pile",pile)
                    
                    # Next, use the ”if“ to divide the two cases.
                    
                    # The first is when humans choose to use the pile1.
                    # Then the computer judges the pile2 first.
                    # If the pile2 is empty.
                    # Judging the pile1.
                    # Once who is the last stone.
                    # Who wins.
                    
                    # The second is when humans choose to use the pile2.
                    # Then the computer judges the pile1 first.
                    # If the pile1 is empty.
                    # Judging the pile2.
                    # Once who is the last stone.
                    # Who wins.
                    
                    if (pile == 1) and (pile1 >= stones):
                        #If it is pile1 and there are enough stones in the pile1.
                        
                        pile1 = pile1 - stones
                        print("Pile 1:",pile1,"   Pile 2:",pile2)
                        
                        if (pile1 <= 0) and (pile2 <= 0):
                            # If the piles are taken empty.
                            
                            human = human + 1  # Humans win the game plus one.
                            print("\nPlayer wins!")
                            print("Score -> human:",human,"; computer:",computer)
                            
                        else:
                            # The stones was not taken by humans.
                            
                            if (pile2 > 0):
                                # If the pile2 is not taken empty.
                                
                                pile2 = pile2 - 1
                                print("Computer -> ",end='')
                                print("Remove 1 stones from pile 2")
                                print("Pile 1:",pile1,"   Pile 2:",pile2)
                                
                            else:
                                # If the pile2 is taken empty.
                                
                                pile1 = pile1 - 1
                                print("Computer -> ",end='')
                                print("Remove 1 stones from pile 1")
                                print("Pile 1:",pile1,"   Pile 2:",pile2)
                                
                            if (pile1 <= 0) and (pile2 <= 0):
                                # The stones was taken empty by computer.
                                
                                computer = computer + 1  # Computer win the game plus one.
                                print("\nComputer wins!")
                                print("Score -> human:",human,"; computer:",computer)
                                
                    if (pile == 2) and (pile2 >= stones):
                        # If it is pile2 and there are enough stones in the pile2.
                        
                        pile2 = pile2 - stones
                        print("Pile 1:",pile1,"   Pile 2:",pile2)
                        
                        if (pile1 <= 0) and (pile2 <= 0):
                            # If the piles are taken empty.
                            
                            human = human + 1  # Humans win the game plus one.
                            print("\nPlayer wins!")
                            print("Score -> human:",human,"; computer:",computer)
                            
                        else:
                            # The stones was not taken by humans.
                            
                            if (pile1 > 0):
                                # If the pile1 is not taken empty.
                                
                                pile1 = pile1 - 1
                                print("Computer -> ",end='')
                                print("Remove 1 stones from pile 1")
                                print("Pile 1:",pile1,"   Pile 2:",pile2)
                                
                            else:
                                # If the pile1 is taken empty.
                                
                                pile2 = pile2 - 1
                                print("Computer -> ",end='')
                                print("Remove 1 stones from pile 2")
                                print("Pile 1:",pile1,"   Pile 2:",pile2)
                                
                            if (pile1 <= 0) and (pile2 <= 0):
                                # The stones was taken empty by computer.
                                
                                computer = computer + 1  # Computer win the game plus one.
                                print("\nComputer wins!")
                                print("Score -> human:",human,"; computer:",computer)
                                
    else:
        play_str = input("\nWould you like to play again? (0=no, 1=yes) ")
        # Judge whether to come again
else:
   print("\nThanks for playing! See you again soon!")# Just the end.
```

## Feedback and suggestions
- E-mail：<liutia20@msu.edu>

---------
Thanks for reading this help document
