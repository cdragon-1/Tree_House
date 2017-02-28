#### number_game(using random.randint)
```python
import random

# generate a random number between 1 and 10
secret_num = random.randint(1, 10)

while True:
    # get a number guess from the player
    guess = int(input("Guess a number between 1 and 10: "))
    # compare guess to secret number
    if guess == secret_num:
        print("You got it! My number was {}".format(secret_num))
        break
    else:
        print("That's not it!")
    # print hit / miss
```
#### number_game_refinement
```python
import random


# safely make in int
# limit guesses
# too high message
# too low message
# play again

def game():
    secret_num = random.randint(1, 10)
    guesses = []

    while len(guesses) < 5:
        try:
            # get a number guess from the player
            guess = int(input("Guess a number between 1 and 10: "))
        except ValueError:
            print("{} isn't a number!".format(guess))
        else:
            # compare guess to secret number
            if guess == secret_num:
                print("You got it! My number was {}".format(secret_num))
                break
            elif guess < secret_num:
                print("My number is higher than {}".format(guess))
            else:
                print("My number is lower than {}".format(guess))
                # print hit / miss
            guesses.append(guess)

    else:
        print("You did'nt get it! My number was {}".format(secret_num))

    play_again = input("Do you want to play again? Y/n ")
    if play_again.lower() != 'n':
        print("Bye!")

game()
```
#### exercise
```python
import random

def random_item(word):
    length = len(word) - 1
    num = random.randint(0, length)
    return word[num]
```
