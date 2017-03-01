#### Monster Game
character.py
```python
import random

from combat import Combat


class Character(Combat):
    attack_limit = 10
    experience = 0
    base_hit_points = 10

    def attack(self):
        roll = random.randint(1, self.attack_limit)
        if self.weapon == 'sword':
            roll += 1
        elif self.weapon == 'axe':
            roll += 2
        return roll > 4

    def get_weapon(self):
        weapon_choice = input("Weapon ([S]word, [A]xe, [B]ow): ").lower()

        if weapon_choice in 'sab':
            if weapon_choice == 's':
                return 'sword'
            elif weapon_choice == 'a':
                return 'axe'
            else:
                return 'bow'
        else:
            return self.get_weapon()

    def __init__(self, **kwargs):
        self.name = input("Name: ")
        self.weapon = self.get_weapon()
        self.hit_points = self.base_hit_points

        for key, value in kwargs.items():
            setattr(self, key, value)

    def __str__(self):
        return '{}, HP: {}, XP: {}'.format(self.name, self.hit_points, self.experience)

    def rest(self):
        if self.hit_points < self.base_hit_points:
            self.hit_points += 1

    def leveled_up(self):
        return self.experience >= 5
```python
monster.py
import random

from combat import Combat

COLORS = ['yellow', 'red', 'blue', 'green']


class Monster(Combat):
    min_hit_points = 1
    max_hit_points = 1
    min_experience = 1
    max_experience = 1
    weapon = 'sword'
    sound = 'roar'

    def __init__(self, **kwargs):
        self.hit_points = random.randint(self.min_hit_points, self.max_hit_points)
        self.experience = random.randint(self.min_experience, self.max_experience)
        self.color = random.choice(COLORS)

        for key, value in kwargs.items():
            setattr(self, key, value)

    def __str__(self):
        return '{} {}, HP: {}, XP: {}'.format(self.color.title(),
                                              self.__class__.__name__,
                                              self.hit_points,
                                              self.experience)

    def battlecry(self):
        return self.sound.upper()


class Goblin(Monster):
    max_hit_points = 3
    max_experience = 2
    sound = 'squeak'


class Troll(Monster):
    min_hit_points = 3
    max_hit_points = 5
    min_experience = 2
    max_experience = 6
    sound = 'growl'


class Dragon(Monster):
    min_hit_points = 5
    max_hit_points = 10
    min_experience = 6
    max_experience = 10
    sound = 'raaaaar'

```
combat.py
```python
import random


class Combat:
    dodge_limit = 6
    attack_limit = 6

    def dodge(self):
        roll = random.randint(1, self.dodge_limit)
        return roll > 4

    def attack(self):
        roll = random.randint(1, self.attack_limit)
        return roll > 4
```
game.py
```python
import sys

from character import Character
from monster import Dragon, Goblin, Troll


class Game:
    def setup(self):
        self.player = Character()
        self.monster = [
            Goblin(),
            Troll(),
            Dragon(),
        ]
        self.monster = self.get_next_monster()

    def get_next_monster(self):
        try:
            return self.monster.pop(0)
        except IndexError:
            return None

    def monster_turn(self):
        if self.monster.attack():
            print("{} is attacking!".format(self.monster))

            if input("Dodge? Y/N ").lower() == 'y':
                if self.player.dodge():
                    print("You got hit anyway!")
                    self.player.hit_points -= 1
            else:
                print("{} hit you for 1 point!".format(self.monster))
                self.player.hit_points -= 1
        else:
            print("{} isn't attacking this turn.".format(self.monster))

    def player_turn(self):
        player_choice = input("[A]ttack, [R]est, [Q]uit? ").lower()
        if player_choice == 'a':
            print("You're attacking {}!".format(self.monster))

            if self.player.attack():
                if self.monster.dodge():
                    print("{} dodged your attack!".format(self.monster))
                else:
                    if self.player.leveled_up():
                        self.monster.hit_points -= 2
                    else:
                        self.monster.hit_points -= 1

                    print("You hit {} with your {}!".format(self.monster, self.player.weapon))
            else:
                print("You missed!")
        elif player_choice == 'r':
            self.player.rest()
        elif player_choice == 'q':
            sys.exit()
        else:
            self.player_turn()

    def cleanup(self):
        if self.monster.hit_points <= 0:
            self.player.experience += self.monster.experience
            print("You killed {}!".format(self.monster))
            self.monster = self.get_next_monster()

    def __init__(self):
        self.setup()

        while self.player.hit_points and (self.monster):
            print('\n' + '=' * 20)
            print(self.player)
            self.monster_turn()
            print('-' * 20)
            self.player_turn()
            self.cleanup()
            print('\n' + '=' * 20)

        if self.player.hit_points:
            print("You win!")
        elif self.monster:
            print("You lose!")
        sys.exit()


Game()
```
