#### 자료형(Data Types)
현재 우리가 관심있게 볼 파이썬의 자료형은 세 가지로, 다음과 같습니다:

- 정수형. Integers (int로 표시),

- 실수형, floats (1.970과 같이 소수점으로 표현하는 분수),  

- 불린. booleans (참과 거짓의 두 가지 값으로 표현)

대개 컴퓨터 프로그램은 데이터를 조작하기 위해 만들어집니다. 그러므로 프로그램에 포함할 수 있는 여러 다른 형태의 데이터(또는 "자료형")을 이해하는 것은 매우 중요합니다.

절대 불린(booleans) 자료형과 따옴표(' 또는 ")를 함께 사용하지 마세요, 그리고 언제나 첫 번째 글자는 대문자로 작성해야 합니다! 파이썬은 대소문자를 구별(case-sensitive)합니다. 따옴표는 문자열(strings)과 함께 사용하며, 다음 단원에서 이에 관해 다루도록 하겠습니다.



```python
>>>round(5.49)
5
>>>round(5.50)
6
>>>int(5.9)
5
문자열로 만들기
>>>str(5)
'5'
>>>'5'
'5'
status_message = "Hey, we have {} people using the site right now"
print(status_message.format(8))
print("Hey, we have {} {} using the site right now".format(5, 'dogs'))

```

**리스트**
```python
In [1]: [1, 2, 3]
Out[1]: [1, 2, 3]

In [2]: my_list = [1, 2, 3]

In [3]: my_list
Out[3]: [1, 2, 3]

In [4]: my_list + 5
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-4-66a66974810d> in <module>()
----> 1 my_list + 5

TypeError: can only concatenate list (not "int") to list

In [5]: my_list + [4, 5]
Out[5]: [1, 2, 3, 4, 5]

In [6]: my_list
Out[6]: [1, 2, 3]

In [7]: my_list += [4, 5]

In [8]: my_list
Out[8]: [1, 2, 3, 4, 5]

In [9]: my_list * 2
Out[9]: [1, 2, 3, 4, 5, 1, 2, 3, 4, 5]

In [10]: my_list *= 2

In [11]: my_list
Out[11]: [1, 2, 3, 4, 5, 1, 2, 3, 4, 5]

In [12]: my_list = [1, 2, 3, 4, 5]

In [13]: my_list.append(6)

In [14]: my_list
Out[14]: [1, 2, 3, 4, 5, 6]

In [15]: my_list.append(7, 8)
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-15-3b696f8580a0> in <module>()
----> 1 my_list.append(7, 8)

TypeError: append() takes exactly one argument (2 given)
append로는 single item만 넣을 수 있음!


In [16]: my_list.append([7, 8])

In [17]: my_list
Out[17]: [1, 2, 3, 4, 5, 6, [7, 8]]

In [18]: my_list = [1, 2, 3]

In [19]: my_list
Out[19]: [1, 2, 3]

In [20]: my_list.extend([4, 5, 6])

In [21]: my_list
Out[21]: [1, 2, 3, 4, 5, 6]

extend로는 2개 이상의 아이템들을 추가할 수 있음

In [22]: list_in_list = [1, 2, 3, [4, 5, 6]]

In [23]: list_in_list
Out[23]: [1, 2, 3, [4, 5, 6]]

In [24]: list_in_list.remove([4, 5, 6])

In [25]: list_in_list
Out[25]: [1, 2, 3]

remove로 리스트 안의 아이템들을 제거

In [26]: list_in_list.remove[2]
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-26-8def016f807c> in <module>()
----> 1 list_in_list.remove[2]

TypeError: 'builtin_function_or_method' object is not subscriptable

In [27]: list_in_list.remove([2])
---------------------------------------------------------------------------
ValueError                                Traceback (most recent call last)
<ipython-input-27-d711fa169ee0> in <module>()
----> 1 list_in_list.remove([2])

ValueError: list.remove(x): x not in list

In [28]: list_in_list
Out[28]: [1, 2, 3]

In [29]: list_in_list.remove(2)

하나의 아이템을 제거할 때는 ()로 입력!

In [31]: str(5)
Out[31]: '5'

In [32]: list(5)
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-32-369ddcb20c00> in <module>()
----> 1 list(5)

TypeError: 'int' object is not iterable

In [33]: list('hello')
Out[33]: ['h', 'e', 'l', 'l', 'o']

In [34]: 'hello'.split()
Out[34]: ['hello']

In [35]: 'hello there students'.split()
Out[35]: ['hello', 'there', 'students']
string을 list로 바꾸기!

In [36]: 'red:blue:green'.split(':')
Out[36]: ['red', 'blue', 'green']
string을 split하기!

In [37]: flavors = ['chocolate', 'mint', 'strawberry']

In [38]: ', '.join(flavors)
Out[38]: 'chocolate, mint, strawberry'
list를 string로 바꾸기

In [39]: "My favorite flavors are: " + ', '.join(flavors)
Out[39]: 'My favorite flavors are: chocolate, mint, strawberry'

In [40]: "My favorite flavors are: {}".format(', '.join(flavors))
Out[40]: 'My favorite flavors are: chocolate, mint, strawberry'


인덱스
In [52]: alpha = 'abcde'

In [53]: alpha.index('a')
Out[53]: 0

In [54]: 'abcabc'.index('a')
Out[54]: 0

In [55]: 'abcabc'.index('b')
Out[55]: 1

In [56]: alpha_list = list(alpha)

In [57]: alpha_list.index('b')
Out[57]: 1

In [58]: alpha
Out[58]: 'abcde'

In [59]: list(alpha)
Out[59]: ['a', 'b', 'c', 'd', 'e']

In [60]: alpha.index('cd')
Out[60]: 2

In [61]: alpha.index('ce')
---------------------------------------------------------------------------
ValueError                                Traceback (most recent call last)
<ipython-input-61-ef09a7b7cc4b> in <module>()
----> 1 alpha.index('ce')

ValueError: substring not found

In [62]: alpha[0]
Out[62]: 'a'

In [63]: alpha_list[2]
Out[63]: 'c'

In [64]: print(alpha)
abcde

In [65]: alpha_list[-1]
Out[65]: 'e'


deleting item

In [66]: trash = 99

In [67]: del trash

In [68]: trash
---------------------------------------------------------------------------
NameError                                 Traceback (most recent call last)
<ipython-input-68-2bb1f4190934> in <module>()
----> 1 trash

NameError: name 'trash' is not defined

In [69]: alpha_list = list('abcde')

In [70]: alpha_list
Out[70]: ['a', 'b', 'c', 'd', 'e']

In [71]: del alpha_list[2]

In [72]: alpha_list
Out[72]: ['a', 'b', 'd', 'e']

In [73]: del alpha_list[1, 2]
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-73-01c37b6facf7> in <module>()
----> 1 del alpha_list[1, 2]

TypeError: list indices must be integers, not tuple

In [74]: alpha = 'abcdef'

In [75]: del alpha[0]
string을 del로 지울 수 없다!
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-75-019c3f6ced57> in <module>()
----> 1 del alpha[0]

TypeError: 'str' object doesn't support item deletion


```
- iterable : member를 하나씩 차례로 반환 가능한 object. 예를 들면 list, str, tuple.




---
<!-- #### 명령문(Statement)이 무엇인가요?
파이썬의 명령문(statement)은 일반 언어의 문장과 비슷하다고 여길 수 있습니다: 이는 의미를 형성하는 언어의 가장 작은 형태입니다. "I", "like", "Spam" 각각은 문장이 될 수 없지만 "I like Spam"은 문장이 될 수 있는 것처럼, 파이썬에서 변수와 자료형 각각은 명령문이 될 수 없어도 이들을 이용해서 명령문을 만들 수 있습니다.

문장에 계속 비유해 보겠습니다. 문장의 시작점과 끝점은 어디고 다른 문장은 어디서 시작하는지를 명백하게 하기 위해선 일종의 구두법이 필요로 합니다. 여러분이 만약 자바 스크립트를 알고 계시면, 각각의 문장이 세미콜론(;)으로 끝난다는 걸 기억하실 겁니다. 파이썬에서는 명령문이 공백(Whitespace)로 구분됩니다. 자바 스크립트에서 여러분이 아무데나 세미콜론을 쓸 수 없는 것처럼, 파이썬에서도 아무데나 여백을 넣을 수 없습니다.

이 공백과 관련해서 익숙해질 필요가 있는데요, 특히 공백의 여부가 상관없는 다른 프로그래밍 언어에 익숙하다면 더욱 더 중요합니다.

인터프리터?
내가 작성한 코드를 받아 구문 오류를 확인하고, 명령문을 실행하는 프로그램. 인터프리터는 컴퓨터와 나 사이에서 중개자 역할을 하며, 내가 컴퓨터에게 내린 지시사항의 결과를 나에게 알린다. -->
