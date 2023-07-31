0728 review
# 함수(function)
## 함수의 선언과 호출
- 함수의 선언
```python
def func_name(parameter1, parameter2,...):
    code1
    code2
    ...
    return value
```
-함수의 호출
```python
func_name(parameter1, parameter2,...)
```
print 도 함수의 예시 (파라메터 개수가 제한이 없음)

```python
dir(__builtins__)
```
파이썬에서 미리 만들어진 함수 호출

### 함수의 return
- 함수가 return 을 만나면 해당 값을 반환하고 함수를 종료
- 만약 return이 없다면 None을 자동으로 반환
- return은 오직 하나의 객체만 반환함.
    - 변수에 할당이 가능하게 함. 
- 바람직한 함수는 정의까지만 하고 그 다음 단계는 다음 코드가 하게끔 하는 함수
- 함수의 목표는 output 값을 내는 것.

## 함수의 인수
### 위치인수 
기본적으로 함수는 인수의 위치로 판단해서 실행

### 기본값
```python
def fun(p1=v1) #변수에 하나를 할당시켜줌
    return v1
```

```python
def greeting(name='익명', age)
    return f'{name}님은 {age}세 입니다.'
```
기본인자가 아닌 ag가 기본인자 뒤에 있다고 에러가 뜸->순서바꿔줘야함

### 키워드 인자
함수를 호출(실행)할 때 내가 원하는 위치에 직접적으로 특정인자를 전달 가능

```python
def greeting(age, name='익명'):
    return f'{name}님은 {age}살입니다.'
print(greeting(10, '홍길동'))
print(greeting(name='홍길동', age = 10))
```
```
print('안녕')
print('안녕','하세요', sep='!', end='?')
``` 

### 가변 인자 리스트

```python
def func(*params):
    pass
```
리스트를 인풋으로 받음 
```python
def my_max(*numbers):
    result = 0
    for number in numbers:
        if result < number:
            result = number 
    return number
```
함수에 인수를 넣지 않거나 여러개 넣을 수도 있다.

### 정의되지 않은 키워드 인자
```python
def func(**kwargs)
    pass
```
여러개의 정의되지 않은 인자를 받을 때 kwargs
```python
def fake_dict(**kwargs):
    for key, value in kwargs.items():
        print(f'{key}는 {value}입니다')
    print(kwargs)
    print(type(kwargs))

fake_dict(korean='안녕', english= 'hello')
```
인자 korean에 '안녕'을 할당, english에 'hello'를 할당하는것

### 딕셔너리를 인자로 넣기(unpacking)
- 인자가 긴 경우 딕셔너리를 선언하고 그 자체로 인자로 넣음
```python
def sign_up(username, password, password_confirmation):       # 회원가입
    if password == password_confirmation:
        print(f'{username}님 회원가입이 완료되었습니다.')
    else:
        print(f'비밀번호가 일치하지 않습니다
my_account = {
    'username': 'asdf1234',
    'password': 'i12w3e4r',
    'password_confirmation': 'i12w3e4r',
}
sign_up(**my_account)
```
### lambda 표현식 

(lambda a, b: a + b)(1, 2)

### 타입힌트
```my_sum(num1: int, num2: int) -> int:
    '''
    두 수의 합을 구하는 함수입니다.
    매개변수 num1, num2를 받아서 num1 + num2 를 return 합니다. 
    '''

    
    return num1 + num2

my_sum(1, 2)
my_sum('1', 2) 
```
단순하게 표기함 하지만 힌트와 다른 타입을 인자로 입력하더라도 코드 실행을 막지는 않음.

### 이름공간(scope)
파이썬에서 사용되는 모든 이름들은 이름공간에 저장되어 있음.

- Local scope : 정의된 함수 내부
- Enclosed scope : 상위 함수
- Global scope : 함수 밖의 변수 혹은 import 된 모듈
- Built-in scope : 파이썬이 기본적으로 가지고 있는 함수 혹은 변수
```
str = '123' -> local scope # 왜 로컬 스코프인지
print (str) 123
str(789) 
-> type error: 'str' object is not callable
del str
str(789) -> '789'
```
## 재귀(recursive)
재귀 함수는 함수 내부에서 자기 자신을 호출하는 함수를 의미한다.

### 팩토리얼 (1 * 2 * ...* n = n!)
*  복잡한 문제를 풀 때 #으로 필요한 연산, 과정을 적으면서 풀기
```
def fact(n):
    result = 1
 # n 이 1이면 결과는 1
    while n > 1:
        result = result * n # result *= n
        n = n-1 # n -= 1

# ex) 3이면 3 * (3-1) *((3-1)-1) 곱하는 수가 1일 때까지 
return result 
fact(5)
```
1! = 1, 2! = 1!* 2 , 3! = 1* 2* 3= 2!*3 =(1!*2)* 3

#### 재귀로 만들어 보기 
```
def factorial(n):
    if n <= 1:
        return 1
    else: 
        return factorial(n-1) * n
```
재귀를 n=1일 때 끝내줘야함 0 을 곱하면 0이되기 때문

###  피보나치 수열
```
F(0) = F(1) = 1
F(n) = F(n-1) + F(n-2)
```

- 재귀버전 
```
def firb_rec(n):
    if n ==1 or n ==0:
        return 1
    else: 
        return fib_rec(n-1) + fib_rec(n-2)
```

- 반복문 버전

```
def fib_loop(n): 
    result = [1, 1]
    for i in range(1,n):
        end1 = result[-1]
        end2 = result[-2]
        fib_num = end1 + end2
        result. append(fib_num)
    return result[-1]
```

# 0731 복습
- print('hello') : 함수
- ''.join(['1','2','3']) : 메소드 
- dir ()-> ()안의 객체가 어떤 기능을 가지고 있는지 확인
    - dir('hello')
    - dir(1)

# 1. 문자열 메소드

```python
a = 'hello my name is minju'
a[0] = 'H' 
```
string 은 immutable하기 때문에 변경할 수 없음 
- a = a.capitalzie() 로 string a를 바꿀 수 있음 a.capitalize()자체는 원본을 바꾸지 않음
- a.title(): 단어 첫 글자마다 대문자로 바꿔짐
- a.upper(): 모든 글자를 대문자로 바꿈
- a.lower(): 모든 글자를 소문자로 바꿈

#### ''.join(iterable): 리스트의 요소들을 하나로 합칠 때
```python
my_list = ['hi', 'my', 'name']
', '.join(my_list)
```
#### .replace(old, new[, count]) []는 써도되고 안써도 됨 기본값이 있음
'wooooooooow'.replace('0', '!', 3) : 'o'를 !로 3개 바꾸겠다. 
-> 'w!!!oooooow'

#### .strip([chars]): 스트링의 양쪽에서 제거함
```python
my_string = '       hello\n'
print(my_string)
print(my_string.strip()) 
```
-> 엔터, 스페이스 다 삭제돼서 hello만 남음

```python
my_str2= 'hihihihihihihellohihihihih'
print(my_string2.strip('hi'))
print(my_string2.strip('h'))
print(my_string2.lstrip('hi')) : 왼쪽만 삭제
print(my_string2.rstrip('hi')) : 오른쪽만 삭제
```

```
ello
ihihihihihihellohihihihih
ellohihihihih
hihihihihihihello
````
ex) hi 를 삭제할 때 h i h i h i 반복되면서 지우다가 h 를 발견했을 때 지우고 i 가 오지 않아서 삭제 중단

#### .find(x)
```
a = 'apple'
- print(a.find('p')): p의 인덱스 값을 가져와줌
- print(a.find('z')): 없으면 -1을 출력 
- 두번째 'p'의 인덱스를 알기 위해서는 
```
for i in range (len(a)):
    if a[i] == 'p':
        print(i)
```

.index(x)
- find와 비슷하지만 index는 없으면 에러가 나옴

.split(x): ()는 무엇을 기준으로 split을 할지, 기본값은 스페이스
#### .count(x): ()의 개수를 세어줌

# 2. 리스트 메소드 

.append(x)
- numbers.append(10): list 에 새 원소값을 추가함 
    - list 는 mutable하므로 원본 자체를 바꿀 수 있음

.extend(iterable): 리스트가 저체로 추가되지 않고 원소들이 나뉘어 들어감
```python
numbers = [1, 2, 4, 5]
a = [99, 100]
numbers.extend(a)
print(numbers)
print(numbers + a) 
```
[1, 2, 4, 5, 99, 100]



#### .insert(idx, x): index 자리에 x를 추가

#### .remove(x): x를 삭제

#### .pop([idx]): 그 위치에 있는 값을 삭제 

#### .sort()
- numbers.sort(): 기본적으로 오름차순
- numbers.sort(reverse = True ): 내림차순

#### .reverse(): 역순으로 만듦
- 슬라이싱으로 똑같이 역순으로 만들기 : numbers= numbers[::-1]

## 2.1 list copy 
python 튜터로 보면 명확하게 보임 


- 리스트 가 다른 변수에 재할당이 될 때는
그 원소들을 가지고 있는 게 아닌 그 원소의 주소들에서 가져옴 
그래서 원래 리스트와 재할당된 리스트는 똑같은 주소에서 가져오고
재할당된 리스트가 변경되면 그 주소에 값을 변경하는 거기 때문에 원래 리스트도 변경되는 것임. 

-이런 상황을 방지하기 위해서는 slicing 을 이용해 새롭게 재할당된 리스트만 변경 가능
b = a[:]

- copy 모듈도 가능
``` 
import copy
a= [1, 2, [3, 4]]
b = copy.deepcopy(a)
b[2][0] = 100 
```

## 2.2 list comprehension
for 문으로 list 를 만들 때 comprehension으로 한줄로 표현 가능
```
result1 =[]
for number in numbers:
    result1.append(number**3)
print(result)

result = [number **3 for number in numbers]
```

# 3. dictionary method
```
info = {
    'name': 'minju'
    'location': 'seoul'
}
```

- info['name'] = 'kang' : name의 value를 바꿈

#### .pop(key[, default])
- print(info.pop('location', None) : None 을 추가하면 삭제할 게 없을 때 None 이 출력 

#### .update(key=value)
```
print(info.get('name'))
print(info.get('school', '123'))
```
```
minju
123 
```
print(info['school']) 은 school 에 해당하는 게 없으니 error 뜸

### 3.1 dict comprehension
# {1: 3. 2: 8, 3: 27}
```
dict={}
for i in range(1, 4):
    dict[i] = i**3
print(dict)

#comp
dict2 ={i: i**3 for i in range(1, 4)}
print(dict2)


# 4. 세트 메소드

#### .add(x): 세트에 하나를 추가할 때, 똑같은 걸 추가해도 한번만 추가됨
#### .update(x): 여러개 추가할 때
- fruit.update('grape') -> 'g' 'r' 'a' 'p' 'e' 이렇게 쪼개서 들어감(string 은 iterable하기 때문에)
- fruit.update({'orange' ,'pear'}) 이렇게 해야 원소가 각각 들어감

#### .remove()
- fruits.remove('orange') 항목 삭제
#### .pop(): 맨앞 값이 삭제됨(세트는 정렬된 데이터가 아니기 때문에 순서가 다 다르게 출력)


# 5. map(), zip(), filter()

## 5.1 map()
```
map(function, iterable)

```
```python
a = [1, 2, 3]
number_str = map(str, a)
print(list(number_str))
```
- function 에는 새로 만든 함수도 가능

## 5.2 zip
```
a = [1, 2, 3]
b = [100, 200, 300]
result = zip(a, b)
print(list(result))
```
[(1, 100), (2, 200), (3, 300)]

## 5.3 filter
```python
filter(function, iterable)
```
- 이때 function 은 T/F를 반환해야 한다.
```python
def is_odd(x):
    return bool(x%2) # 홀수이면 true 반환
numbers = [1, 2, 3, 4, 5]
result = filter(is_odd, numbers)
print(list(result))
```
True 인 원소들만 남음
