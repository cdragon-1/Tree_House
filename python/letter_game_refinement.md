```python
import os
import random
import sys

words = [
    'apple',
    'banana',
    'orange',
    'coconut',
    'strawberry',
    'lime',
    'grapefruit',
    'lemon',
    'kumquat',
    'blueberry',
    'melon',
]


def clear():
    if os.name == 'nt':
        os.system('cls')
    else:
        os.system('clear')


def draw(bad_guesses, good_guesses, secret_word):
    clear()

    print('Strikes: {}/7'.format(len(bad_guesses)))
    print('')

    for letter in bad_guesses:
        print(letter, end='')
    print('\n\n')

    for letter in secret_word:
        if letter in good_guesses:
            print(letter, end='')
        else:
            print('_', end='')

    print('')


def get_guess(bad_guesses, good_guesses):
    while True:
        guess = input("Guess a letter: ").lower()

        if len(guess) != 1:
            print("You can only guess a single letter!")
        elif guess in bad_guesses or guess in good_guesses:
            print("You've already guess that letter!")
        elif not guess.isalpha():
            print("You can only guess letters!")
        else:
            return guess


def play(done):
    clear()
    secret_word = random.choice(words)
    bad_guesses = []
    good_guesses = []

    while True:
        draw(bad_guesses, good_guesses, secret_word)
        guess = get_guess(bad_guesses, good_guesses)

        if guess in secret_word:
            good_guesses.append(guess)
            found = True
            for letter in secret_word:
                if letter not in good_guesses:
                    found = False
            if found:
                print("You win!")
                print("The secret word was {}".format(secret_word))
                done = True
        else:
            bad_guesses.append(guess)
            if len(bad_guesses) == 7:
                draw(bad_guesses, good_guesses, secret_word)
                print("You lost!")
                print("The secret word was {}".format(secret_word))
                done = True
        if done:
            play_again = input("Play again? Y/n ").lower()
            if play_again != 'n':
                return play(done=False)
            else:
                sys.exit()


def welcome():
    start = input("Press enter/return to start or Q to quit ").lower()
    if start == 'q':
        print("Bye!")
        sys.exit()
    else:
        return True


print('Welcome to Letter Guess!')

done = False

while True:
    clear()
    welcome()
    play(done)

```
#### exercise
Use input() to ask the user if they want to start the movie.
If they answer anything other than "n" or "N", print "Enjoy the show!". Otherwise, call sys.exit(). You'll need to import the sys library.
```python
import sys

start = input("Do you want to watch a movie? ").lower()
if start == 'n':
    sys.exit()
else:
    print("Enjoy the show!")
```
#### exercise_2nd
Alright, last step but it's a big one.
Make a while loop that runs until start is falsey.
Inside the loop, use random.randint(1, 99) to get a random number between 1 and 99.
If that random number is even (use even_odd to find out), print "{} is even", putting the random number in the hole. Otherwise, print "{} is odd", again using the random number.
Finally, decrement start by 1.
I know it's a lot, but I know you can do it!
```python
import random

def even_odd(num):
       # If % 2 is 0, the number is even.
        # Since 0 is falsey, we have to invert it with not.
    return not num % 2

start = 5
while start != 0:
    num = random.randint(1, 99)
    checked_num = even_odd(num)
    if  checked_num == True:
        print("{} is even".format(num))
    else:
        print("{} is odd".format(num))
    start -= 1

```
