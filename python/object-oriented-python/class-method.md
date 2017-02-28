#### class & attribute
```python
class Monster:
    hit_points = 1
    color = 'yellow'
    weapon = 'sword'
    sound = 'roar'

    def battlecry(self):
        return self.sound.upper()
```
Functions that belong to classes though are called **methods**.
(Functions = methods) in classes
self는 항상 내가 method 상에서 부른 instance를 대표한다.

#### \_\_init__(self):
```python
class Monster:
    def __init__(self, hit_points=5, weapon='sword', color='yellow', sound='roar'):
        self.hit_points = hit_points
        self.weapon = weapon
        self.color = color
        self.sound = sound

    def battlecry(self):
        return self.sound.upper()
```
#### self, default value
```python
class Monster:
    def __init__(self, **kwargs):
        self.hit_points = kwargs.get('hit_points', 1)
        self.weapon = kwargs.get('weapon', 'sword')
        self.color = kwargs.get('color', 'yellow')
        self.sound = kwargs.get('sound', 'roar')


    def battlecry(self):
        return self.sound.upper()
```
