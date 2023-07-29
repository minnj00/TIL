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