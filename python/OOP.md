# 객체지향 프로그래밍(OOP)
- 클래스: 같은 종류의 집단의 속성(attribute)과 행위(method)를 정의한 것 
- 인스턴스: 클래스를 실제로 메모리상에 할당한 것
- 속성: 클래스/인스턴스가 가지고 있는 데이터/값
- 행위: 클래스/인스턴스가 가지고 있는 함수/기능

```
number = 1 + 2j
print(number.real)
print(number.imag)
print(type)
```
- n 은 속성과 행위로 나뉘는데 , 속성에는 real:1, imag:2 이런 정보가 담겨있음.
- 타입은 complex 라고 하는 클래스라고 출력됨.

```
my_list = [1, 2, 3, 4, 5]
print(type(my_list))
my_list.sort()
```
- my_list 는 속성부분과 행위부분으로 나뉘는데 행위부분 중 .sort()과 같은 것들이 있음 (행위를 호출하기때문에 ()가 붙여짐)

```
예를들어 
핸드폰에 대한 정보를 코드로 정리한다고 할 때
power = False
number = '010-1234-1234'
book = {
    '홍길동': '010',
    '이순신': '010',
}
model = 'iphone12'
class 가 없다면 이렇게 모든 속성들을 다 적어야 함
폰이 여러개라면 각각의 폰마다 적어줘야함. 
```


# Class 
- 클래스 선언 
```
class ClassName:
    attribute = value

    def method_name(self):
        code 
```

- 인스턴스화 
ClassName()

```
ex) 
#선언
class MyClass:
    name = 'kim'

    def hello(self):
        return 'hello'

#인스턴스화
a = MyClass()

print(a.name) # 괄호가 없는 상태로 실행
print(a.hello()) #괄호 붙여서 실행 


```

- my_phone.number = '01032' => 클래스가 할당된 my_phone(인스턴스)의 정보를 바꿀 수 있음
- your_phone.number 의 데이터는 다른 공간에 있으므로 영향을 받지 않음.

```
class Person: # => 클래스 정의 (선언) : 클래스 객체  생성
    name = 'kim' # => 속성(attribute): 변수/값/데이터

    def hello(self): # => 행동(method): 함수/기능
        return self.name

p= Person() #인스턴스화/ 인스턴스 객체를 생성
p.name # 속성을 호출 
p.hello() # 메소드를 실행
```
- self: 인스턴스 객체 자기자신(다른 언어에서는 this)
- 특별한 상황을 제외하고는 무조건 메소드의 첫번째 인자로 설정한다.
- 인스턴스 메소드를 실행할 때 자동으로 첫번째 인자에 인스턴스를 할당한다(따로 입력하지 않아도 됨) 

```
ex 
class Person(): # 상속을 하지 않게 되면 () 생략 가능 
    name = ''

    def hello(self):
        print(f'나의 이름은 {self.name} 입니다.')

p1 = Person()
Person.hello(p1) # Person 이라는 class 에서 hello 라는 메소드를 선택하고 p1을 인자로 넣음. 
p1.hello() #p1인스턴스 객체에서부터 메소드가 실행되므로 자동으로 self에 p1을 할당. 위와달리 인자로 p1넣는 것을 생략함. 

```

## 생성자, 소멸자
```python
def __init__(self): #인스턴스화를 할 때 설정하는 것
    pass
    
def __del__(self):
    pass
```
- __init__ 은 자주 쓰지만 del은 거의 쓸 일이 없을 것.

```
ex)
class Person:
    name = 'noname'
    def __init__(self, name = '익명'): #인스턴스화를 할 떄
        self.name = name
        print('생성됨')
        
    def __del__(self): #소멸될 때 
        print('소멸됨') 
        
p1 = Person() # => Person.__init__(p1) 생성될 때 실행하는 함수이기 때문에 
p2 = Person('Kim') 
# 처음 인스턴스에 할당할 때부터 name인자를 넣어줌. self 에 p2가 들어가고 name 에 'kim'이 들어감.
```

## 클래스변수
- 클래스 선언 블록 최상단에 위치
## 인스턴스변수
- 인스턴스 내부에서 생성한 변수 (self.variable=)

```python
class TestClass:
    class_variable = '클래스변수'

    def __init__(self, arg):
        self.instance_variable = '인스턴스변수'

    def status(self):
        return self.instance_variable
```
```
ex)

class Person: 
    name = '홍길동'
    phone = '010-1234-1234'
    

    def __init__(self, name):
        self.name = name


p = Person('강민주') #인스턴스 변수에  '강민주' 할당
print(p.name) #인스턴스 변수에 할당한 강민주가 나옴
print(Person.name) #이것은 클래스 변수를 호출한 것 
print(p.phone)  # 먼저 인스턴스 변수에서 phone을 찾지만 없으므로 이 때는 class 변수에서 가져옴. __init__이 없는 클래스를 할당한 인스턴스 변수도 모두 경우가 같음.
# print(p.location) #하지만 location 은 아무곳에도 없음 
```

## 클래스메소드, 인스턴스메소드, 스태틱메소드 

```python
class MyClass:
    def instance_method(self): 
        pass
    @classmethod
    def class_method(cls): #cls를 넣어서 classmethod가 아니라 @classmethod를 적었기 떄문에 
        pass
    @staticmethod
    def static_method():
        pass 
```
```python

class Puppy:
    num_of_puppy = 0  # 모든 인스턴스에서 접근 가능

    def __init__(self, name): # 어느 인스턴스에 인스턴스화가 됐을 때 실행됨.
        self.name = name
        Puppy.num_of_puppy += 1
    @classmethod
    def get_status(cls):
        return f'현재 강아지는 {cls.num_of_puppy}마리 입니다.'
    @staticmethod # 인스턴스 변수와 클래스 변수를 이용할 필요가 없을 때 사용
    def bark(string='멍멍'):
        return string 

# 인스턴스메소드에서 클래스변수를 수정할 수 없다는 것이 아님. 보통 서로 침범하지 않도록 작성함
```
## 상속
```python
class Person:

    def __init__(self, name):
        self.name = name

    def greeting(self):
        print(f'안녕하세요 {self.name}입니다.')
```
```python
class Student(Person):
    # Person 이 Student 에 상속됨. 
    # def __init__(self, name):
    #     self.name = name

    # def greeting(self):
    #     print(f'안녕하세요 {self.name}입니다.')
    
    def __init__(self, name, student_id):
        self.name = name
        self.student_id = student_id
        # __init__ 에 새로운 인자를 추가.

class Solider(Person):

    def greeting(self):
        return f'충성! {self.name}입니다.' 
        # greeting 함수에 새로 덮어씌워짐.
        
```
```
class Baby(Mom, Dad):
    pass
```
이렇게 다중으로도 상속가능



