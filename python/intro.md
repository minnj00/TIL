# intro

## 단축키 
- command + enter: 현재 셀 실행
- shift + enter: 지금 셀 실행 & 아래로 이동
- option + enter : 지금 셀 실행 & 아래에 새로운 셀 추가
- b: 아래에 새로운 셀 생성
- m: 마크다운 셀로 전환
- y: 코드 셀로 전환

## 주의사항 

- 대문자/ 소문자
- 띄어쓰기
- 스펠링 주의

## 1. 변수
- 변수이름은 어떤 이름이든 상관 없음
- 다만 우린 앞으로 영어, 숫자, _ 를 이용하여 선언 
- 키워드 사용불가 

```
import keyword
keyword.kwlist 
```
이 리스트에 있는 키워드들은 변수이름으로 선언 불가

### 1.1 number
- int: 정수
- float: 실수
- complex: 복소수
- a.imag: 복소수 a의 허수 부분을 반환
- a.real: 복소수 a의 실수 부분을 반환
* 어떤 데이터 안에 접근을 할 때 .을 사용

### 1.2 Boolean
True, False 로 이루어짐
```
a = True
type(a) 
Boolean 으로 확인
```
0과 1은 각각 False, True로 출력
bool(0) -> False, bool(1) -> True

bool() ()안이 비어있으면 False, 뭐라도 있으면 True

### 1.3 None
```
a = None 
type(a)
NoneType으로 출력
```
### 1.4 string

- 문자열은 `'` `"`를 이용하여 표현
```
a = 'hello'
type(a)
str (결과)
```
- pep 8 규칙에 따르면 한번 작은 따옴표로 적으면 모든 코드를 적을 때 작은 따옴표로 통일하기! (style guide는 또 회사마다 다름)

- input: 사용자가 어떤 데이터를 입력할 수 있게 하는 기능을 함. 
    - 이때 어떤 데이터 형식이든 string 으로 인식함. (숫자값을 받기위해서는 int()같은 것을 씌워 형태를 변환해줘야함)
```
print ('안녕하세요? '강민주' 입니다')
```
이때 우리가 저 문장(문자열)을 넣기 위해 쓴 맨 앞과 맨 끝 따옴표 말고 
다른 따옴표는 작성앞에 백슬래쉬를 입력. 홑따옴표의 기능을 상실시킴.(escape 문자열)

- \n: 뉴라인 생성(다음줄)
- \t: tab(들여쓰기)
- end = '!': 마지막에 느낌표 붙이기
- sep: 중간에 넣음, 디폴트 값은 빈칸

#### string interpolation

1. %-formatting
2. str.format()
3. f-string
거의 세번째만 슴


print(f'홍길동은 {age}살 입니다.')

## 2. 연산자 
### 2.1 연산자

| 기호 | 의미 |
| :---: | :---: |
| + | 더하기 |
| - | 빼기 |
| * | 곱하기 |
| / | 나누기 |
| ** | 제곱 |
| // | 나눈 몫 |
| % | 나머지 값 |
| divmod() | 몫, 나머지 |

### 2-2. 비교연산자

연산자 왼쪽 값 기준

| 기호 | 의미 |
| :---: | :---: |
| > | 더 크다 |
| < | 더 작다 |
| >= | 크거나 같다 |
| <= | 작거나 같다 |
| == | 동일하다 |
| != | 동일하지 않다 |

- 연산자 왼쪽 값을 오른쪽 값과 비교한 결과로 `True`, `False`로 나옴
- `==` 는 문자도 비교 가능



### 2.3. 논리연산자

- `and` : 양쪽 모두 True일 때 `True` 출력
- `or` : 양쪽 모두 False일 때 `False`
- `not` : 반대값 반환


 단축평가

`and` 
- 앞이 True : 뒷값 출력 (앞이 True면 뒤에가 True 면 True, False 면 False 출력 -> 뒷값)
 
- 앞이 False : 앞값 출력 (뒷값에 상관 없이 무조건 False기 때문에)

`or`
- 앞이 True : 앞값 출력 (하나라도 True 면 True 니깐 그냥 앞 출력)

- 앞이 False : 뒷값 출력 (뒤가 False 여야 False 출력이니깐 뒷값)


### 2.4. 복합연산자

연산자 내용을 바로 적용하고 할당

| 일반연산자 | 복합연산자 |
| :--: | :--: |
| a = a + b | a += b |
| a = a - b | a -= b |
| a = a ** b | a **= b |

### 2.5 기타연산자

- concetenation: 두 가지 데이터를 연결
'hi' 와 'hello' 두 스트링을 + 로 연결하면 'hihello'
[1, 2, 3] 와 [4, 5, 6] 두 리스트를 + 로 연결하면 [1, 2, 3, 4, 5, 6]

- containment
```
print('a' in 'apple')
print(1 in [1, 2, 3])
```
True 나 False 로 출력됨.

- identity
```
a = 123123
b = 123123
print(a is b)
print(id(a))
print(id(b))
```
False 로 출력되고 다른 주솟값이 출력됨.

#### 연산자 우선순위
0. ()를 통해 그룹
1. **
2. 산술연산자(*,/)
3. 산술연산자(+,-)
4. 비교연산자, in, is
5. not
6. and
7. or

print(-3 ** 4) # 3의 4제곱에 - 를 붙임(제곱 먼저 계산된 후 - 기호가 붙는거)
- -81 로 출력

## 3. 형변환
### 3.1 암시적 형변환

```
a = True
b = False
c =1 
print(a + c) # true 를 자동으로 1로 변환
print(b + c)
```
출력값 
```
2
1
```
int 와 complex 도 + 가능

### 3.2 명시적 형변환
- int(): 하지만 실수는 int 를 씌운다고 변환할 수 없음
- float()
- str(): int 와 str 을 연결할 수 없을 때 int를 str으로 변환
- bool() : ()안에 데이터가 뭔가 있으면 True

## 4. 시퀀스(sequence) 자료형
데이터의 순서대로 나열된 자료구조.

1. 리스트
2. 튜플
3. 레인지
4. 문자열

### 4.1 List(배열)
- 선언: 변수이름 = [value1, value2, value3, ...]
- 접근: 변수이름[index]

### 4.2 Tuple
- 선언 : 변수이름 = (value1, value2, value3)
- 접근 : 변수이름[index]
- 리스트와 유사하지만 수정 불가능(immutable)하다. (t[2]=5 불가능)

### 4.3 range
- range(n) : 0 부터 n-1까지 범위
- range(n, m) : n 부터 m-1까지 범위
- range(n, m, s) :n 부터 m-1까지 +s만큼 증가하는 범위
print(list(range(n))) 으로 출력

### 4.4 String
### 4.5 시퀀스에서 활용가능한 연산/ 함수
- indexing
```
print(my_list[1])
print(my_tuple[1])
print(my_range[1])
print(my_string[1])
```

- slicing
```
print(my_list[1:3]) # 1번째부터 3번째 전까지
print(my_tuple[1:3])
print(my_range[1:3])
print(my_string[1:3])
my_range[2:6:2]: 2에서 5까지 2 간격으로
```
- in
```
print(1 in my_list)
print(1 in my_tuple)
print(1 in my_range)
print('1' in my_string)  # not in 도 가능
```

- concatenation
print(my_list + [1, 2, 3]

- *
```
print([0] * 10)
print([[0] * 10] *10)
```
- len(my_list)
- min(my_list)
- my_list.count(1) : 원하는 숫자가 몇번 등장하는지

## 5. 시퀀스데이터가 아닌 자료구조

### 5.1 Set 
수학에서 사용하는 집합과 동일하게 처리 (중복된 값이 없음)
- 선언 : 변수이름 = {value1, value2, value3...}

- my_set_a - my_set_b
- my_set_a | my_set_b # 합집합기호 | (파이프)
- my_set_a & my_set_b # 교집합

- 반복되는 값을 없애고 다시 리스트로 만들고 싶을 때
list(set(my_list))

### 5.2 Dictionary 

- 선언 : 변수이름 = {key1: value1, key2: value2,...}
    - #pep 8에 따르면 key와 콜론 붙여쓰고 value전엔 띄어쓰기
- 접근: 변수이름[key]

- dictionary는 key와 value가 쌍으로 이루어져있다.
- key에는 immutable한 모든 것을 사용 가능 (불변값: string, integer, boolean, tuple,...)
- value에는 모든 데이터 가능(list, dictionary도 가능) 

- 같은 key 가 두 번 선언될 경우 마지막 value로 선언됨
- dict_a.keys(): key 들 출력
- dict_a.values(): value 들 출력






