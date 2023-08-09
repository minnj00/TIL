# Linked List
파이썬은 리스트의 용량을 정해놓지 않고 가변적이기 때문에 잘 쓰이진 않을 것임.
## 순차 리스트 
## 연결리스트
새로운 원소를 삽입할 때 그 위의 원소의 주소를 값을 바꿔줌 (잘 이해안됨)

## 삽입정렬 
정렬이 안된 부분의 원소를 뽑아서 정렬된 곳의 적절한 위치에 넣음.
## 병합정렬 
- 최소크기의 부분집합이 될 때까지 분할을 계속하고, 둘씩 비교해서 위치를 바꿈.

### 파이썬 queue 
- 파이썬에서는 queue를 리스트로 표현함
- pop을 사용하게 되는데 메모리 값을 많이 씀. 
    - 0번째 공간이 빠졌을 때, 모든 요소를 앞으로 당기는 연산을 함. (ex, 100개의 원소가 있으면 99번 연산을해야해서 시간이 걸림)
    - 그래서 deque 라는 라이브러리로 조금 더 빠르게 처리할 수 있음. 