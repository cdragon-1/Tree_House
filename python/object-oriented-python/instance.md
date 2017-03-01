#### instance
```python
class Character:
    experience = 0
    hit_points = 10

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

        for key, value in kwargs.items():
            setattr(self, key, value)
```
#### exercise
Add a score method to Game that takes a player argument. The player argument will be either 1 or 2. Increase that player's value in self.current_score by 1. You'll need to adjust the index (i.e. player = 1 means self.current_score[0] needs to increase).
```python
class Game:
    def __init__(self):
    self.current_score = [0, 0]

    def score(self, player):
        if player == 1:
            self.current_score[0] += 1
        elif player == 2:
            self.current_score[1] += 1

```
> sources are from TeamTreehouse
