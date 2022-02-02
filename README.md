# game
import random
from random import randint as rint
from collections import Counter
import time
import os
lives = 3
points = 0


print("Your name for this game is going to be ...")
time.sleep(2)
Fname = "Bob"
Sname = "Smith"
Fullname = Fname + " " + Sname
print(Fullname)
time.sleep(2)

# After enterance code
print("So " +str(Fullname)+ " are you ready to play?")
answer = input("")
if answer.lower() == "yes" or answer.lower() == "y":
    print("You will now commence the game")
if answer.lower() == "no" or answer.lower() == "n":
    exit()



dice1 = (9)
dice2 = (3)
dice3 = dice1 + dice2 * 2
dice4 = dice1/dice2
            
#Intro instructions
            
print("Hello " +Fullname+ " You are about to play a dice guessing game")
time.sleep(2)
print("Basically what you have to do is guess the answer to 2 dice that have been rolled and if you get it correct then you get points")
print("If you get an answer wrong then you lose a the only life you have")

#This is the instructions for what will happen when the dice rolls
time.sleep(3)
print("So basically " +Fullname+ " this is how it works")
print("If the dice that are rolled are the same then the numbers will have been added together then timesed by 2")
time.sleep(2)
print("If the dice that are rolled are not the same then the numbers have been divided by each other")
time.sleep(2)
input("Are you ready to start: ")
print("Dice 1 is " +str(dice1))
time.sleep(2)
print("Dice 2 is " +str(dice2))
answer = input("Enter what you think the answer is: ")

#What happens when answer is correct
if answer == "3":
    print("Well done you got the answer correct")
    points = points + 50
    print("You now have " +str(points)+ " points")
    print("Congrats " +Fullname+ " You have succeeded in passing the challenge")
    time.sleep(2)
# Next Stage
print("There are now two games you can play")
print("Number 1 is noughts and crosses")
time.sleep(2)
print("Number 2 is Hangman")
time.sleep(2)
print("Noughts and crosses will not be against an AI so you need another player for it")
time.sleep(2)
print("Hangman is a 1 player game where computer makes up a word and you have to guess it")
time.sleep(2)
print("So what is it that you are choosing to do?")
answer = input ("")
if answer == "1":      
    
    board = [' ',' ',' ',' ',' ',' ',' ',' ',' ',' ']    
    player = 1    
       
    ########win Flags##########    
    Win = 1    
    Draw = -1    
    Running = 0    
    Stop = 1    
    ###########################    
    Game = Running    
    Mark = 'X'    
       
    #This Function Draws Game Board    
    def DrawBoard():    
        print(" %c | %c | %c " % (board[1],board[2],board[3]))    
        print("___|___|___")    
        print(" %c | %c | %c " % (board[4],board[5],board[6]))    
        print("___|___|___")    
        print(" %c | %c | %c " % (board[7],board[8],board[9]))    
        print("   |   |   ")    
       
    #This Function Checks position is empty or not    
    def CheckPosition(x):    
        if(board[x] == ' '):    
            return True    
        else:    
            return False    
       
    #This Function Checks player has won or not    
    def CheckWin():    
        global Game    
        #Horizontal winning condition    
        if(board[1] == board[2] and board[2] == board[3] and board[1] != ' '):    
            Game = Win    
        elif(board[4] == board[5] and board[5] == board[6] and board[4] != ' '):    
            Game = Win    
        elif(board[7] == board[8] and board[8] == board[9] and board[7] != ' '):    
            Game = Win    
        #Vertical Winning Condition    
        elif(board[1] == board[4] and board[4] == board[7] and board[1] != ' '):    
            Game = Win    
        elif(board[2] == board[5] and board[5] == board[8] and board[2] != ' '):    
            Game = Win    
        elif(board[3] == board[6] and board[6] == board[9] and board[3] != ' '):    
            Game=Win    
        #Diagonal Winning Condition    
        elif(board[1] == board[5] and board[5] == board[9] and board[5] != ' '):    
            Game = Win    
        elif(board[3] == board[5] and board[5] == board[7] and board[5] != ' '):    
            Game=Win    
        #Match Tie or Draw Condition    
        elif(board[1]!=' ' and board[2]!=' ' and board[3]!=' ' and board[4]!=' ' and board[5]!=' ' and board[6]!=' ' and board[7]!=' ' and board[8]!=' ' and board[9]!=' '):    
            Game=Draw    
        else:            
            Game=Running    
        
    print("Tic-Tac-Toe Game Designed By Stephen Dean")
    print("Also the creater of this entire game")
    print("Player 1 [X] --- Player 2 [O]\n")    
    print()    
    print()    
    print("Please Wait...")    
    time.sleep(3)    
    while(Game == Running):    
        os.system('cls')    
        DrawBoard()    
        if(player % 2 != 0):    
            print("Player 1's chance")    
            Mark = 'X'    
        else:    
            print("Player 2's chance")    
            Mark = 'O'    
        choice = int(input("Enter the position between [1-9] where you want to mark : "))    
        if(CheckPosition(choice)):    
            board[choice] = Mark    
            player+=1    
            CheckWin()    
        
    os.system('cls')    
    DrawBoard()    
    if(Game==Draw):    
        print("Game Draw")    
    elif(Game==Win):    
        player-=1    
        if(player%2!=0):    
            print("Player 1 Won")    
        else:    
            print("Player 2 Won")

if answer == "2":
# Hangman
    someWords = '''apple banana mango strawberry 
orange grape pineapple apricot carrot sprout lettuce cauliflower
onion tomato sweetcorn potato'''
  
someWords = someWords.split(' ')
# randomly choose a secret word from our "someWords" LIST.
word = random.choice(someWords)         
  
if __name__ == '__main__':
    print('Guess the word! HINT: word is a name of a fruit or a vegetable')
      
    for i in word:
         # For printing the empty spaces for letters of the word
        print('_', end = ' ')        
    print()
  
    playing = True
     # list for storing the letters guessed by the player
    letterGuessed = ''                
    chances = len(word) + 2
    correct = 0
    flag = 0
    try:
        while (chances != 0) and flag == 0: #flag is updated when the word is correctly guessed 
            print()
            chances -= 1

  
            try:
                guess = str(input('Enter a letter to guess: '))
            except:
                print('Enter only a letter!')
                continue
  
            # Validation of the guess
            if not guess.isalpha():
                print('Enter only a LETTER')
                continue
            elif len(guess) > 1:
                print('Enter only a SINGLE letter')
                continue
            elif guess in letterGuessed:
                print('You have already guessed that letter')
                continue
  
  
            # If letter is guessed correctly
            if guess in word:
                k = word.count(guess) #k stores the number of times the guessed letter occurs in the word
                for _ in range(k):    
                    letterGuessed += guess # The guess letter is added as many times as it occurs
  
            # Print the word
            for char in word:
                if char in letterGuessed and (Counter(letterGuessed) != Counter(word)):
                    print(char, end = ' ')
                    correct += 1
                # If user has guessed all the letters
                elif (Counter(letterGuessed) == Counter(word)): # Once the correct word is guessed fully, 
                                                                # the game ends, even if chances remain
                    print("The word is: ", end=' ')
                    print(word)
                    flag = 1
                    print('Congratulations, You won!')
                    break # To break out of the for loop
                    break # To break out of the while loop
                else:
                    print('_', end = ' ')
  
              
  
        # If user has used all of his chances
        if chances <= 0 and (Counter(letterGuessed) != Counter(word)):
            print()
            print('You lost! Try again..')
            print('The word was {}'.format(word))
  
    except KeyboardInterrupt:
        print()
        print('Bye! Try again.')
        exit()

    
    

