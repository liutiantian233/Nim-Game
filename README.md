# Nim Game

@[TianTian|MSU Computer Science Student]

**Nim** is a mathematical game of strategy in which two players take turns removing objects from distinct piles. The game will be played between the human player and the computer player. In this project, you will handle the computer player while a user plays the game. Choosing the optimal game strategy is complicated and will likely require you to do things that we have not covered yet. We will use a simplified version here.

**Learning Objectives**
- integers (int)
- conditionals
- iteration
- input and output

-------------------

## Nim Game Introduction

>Nim is a mathematical game of strategy in which two players take turns removing objects from distinct heaps or piles. On each turn, a player must remove at least one object, and may remove any number of objects provided they all come from the same heap/pile. The goal of the game is to be the player who removes the last object.    —— [Wikipedia](https://en.wikipedia.org/wiki/Nim)

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
