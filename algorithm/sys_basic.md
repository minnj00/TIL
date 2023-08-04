txt 파일을 불러와서 저장
```python
import sys
sys.stdin = open('input.txt') 
```

TC = int(input()) 보통 첫번째 수가 반복해야할 횟수임.

for i in range(TC): TC만큼 반복하기 위한 for 문 

   
- 1차원 리스트 input 받기

```python
numbers = input().split()
for number in numbers:
    int_num = int(number)

    if int_num % 2 ==1:
        print (f'{int_num}은 홀수 입니다.')
```
아니면 

```python
numbers = list(map(int,input().split()))
```

- 2차원 리스트 input 받기
```python
N = int(input()) # row N 
matrix = []

for i in range(N):
    numbers = list(map(int,input().split()))
    matrix.append(numbers)
    
```


