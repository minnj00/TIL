# 1. 모듈

- fibo 라는 새로 만든 모듈을 가져오기
```
import fibo 
print(fibo): fibo 가 저장된 위치가 나옴
fibo.fib_loop(4) 
```
# !! 이때 잠깐 에러가 떴는데 
restart kernal and clear outputs of all cells 하니깐 해결됨

# 2. 패키지

```
my_Package/
    __init__.py
    math/
        __init__.py
        fibo.py
        formula.py

```
- 패키지 안에 `__init__.py` 파일이 있어야 패키지로 인식 
- 보통 변수 이름을 지을 때 언더바로 짓고 모듈 만들때는 camelCase 
- snake, pascal, camel 만 중요

### 패키지에서 필요한 모듈을 꺼내오는 코드 

```
import myPackage
from myPackage.math import formula
``` 
폴더의 경로를 적어줌 (myPackage폴더 안의 math라는 폴더 안의 formula를 가져옴)

formula.pi , formula.my_max(1, 2)

### 경로에 있는 모듈이 가지고 있는 모든 변수, 함수를 추가
from myPackage.math.fibo import * 
# 이 경로로 fibo라는 파일에 접근해서 전체를 다 가져옴

```
formula = 1234
from myPackage.math import formula

print(formula)
```

# 이름이 겹치기 때문에 모듈이 불러와짐 
# 이런 경우는 좋지 않으므로 뒤에 불러와진 모듈이름을 바꾸는 게 좋음

#위에 대한 예시
```
formula = 1234
from myPackage.math import formula as f 

print(formula)
print(f)
```

# 3. 파이썬 내장 패키지
## 3.1 math
```
import math
math.pi
math.e
math.ceil(pi) # 반올림
math.floor(pi) # 반내림
math.sqrt(9) #제곱근
```

## 3.2 random 
``` 
import random
- random.random() : 랜덤의 소수를 출력
- random.randint() : 랜덤으로 정수를 출력
```

### seed
random.seed(1) #우리가 랜덤이라고 부르는 것을 컴퓨터는 계산을 해서 내보낸다
seed 를 하나로 계속 정해서 코드를 시행하면 같은 수가 나옴

### shuffle
``` 
a= [1, 2, 3, 4, 5]
random.shuffle(a)
```

### choice
- random.choice(<list>): 원소 중 하나를 랜덤으로 뽑음

### sample
```
a = rnage(1, 46)
random.sample(a, 6)
```
6개를 랜덤으로 추출

## 3.3 datetime

### from datetime import datetime : datetime 안의 datetime 모듈을 불러옴
- now = datetime.now()
- today = datetime.today()
- utc = datetime.utcnow() : 그리니치 기준
- now.strftime('%Y년'): '2023년'
- now.strftime('%Y/%m/%d'): '2023/07/31'
- now.year : 2023
- now.day : 31
- now.weekday(): 0~6 -> 월~일
- birth = datetime(2023, 1, 1): 특정 날짜값을 선언

### from datetime import timedelta 
: timedelta 모듈 불러옴

- future = timedelta(days=3) : 시간을 더할 때 사용
    - print(birth + future): datetime.datetime(2023, 1, 4, 0, 0)

```
christmas = datetime(2023, 12, 25)
christmas - now
``` 
datetime.timedelta(days=146, seconds=27533, microsecons=876507)