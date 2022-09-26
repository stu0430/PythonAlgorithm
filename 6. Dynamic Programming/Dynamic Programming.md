# 다이나믹 프로그래밍 

## 중복되는 연산을 줄이자

- 컴퓨터는 연산 속도에 한계가 있고, 메모리 공간을 사용할 수 있는 데이터의 개수도 한정적 -> 연산 속도와 메모리 공간을 최대한 활용할 수 있는 효율적 알고리즘 필요
- 메모리 공간을 약간 더 사용해 연산 속도 비약적인 증가 -> `다이나믹 프로그래밍`

```python
# 피보나치 함수를 재귀 함수로 구현
def fibo(x):
    if x == 1 or x == 2:
        return 1
    return fibo(x - 1) + fibo(x - 2)

print(fibo(4))

```

- f(n) 함수에서 n이 커질수록 수행 시간이 기하급수적으로 늘어남 (동일한 함수의 반복 호출)
- `다이나믹 프로그래밍`의 조건
  - 1. 큰 문제를 작은 문제로 나눌 수 있다.
  - 2. 작은 문제에서 구한 정답을 그것을 포함하는 큰 문제에서도 동일하다.
- `메모이제이션` : `다이나믹 프로그래밍` 구현 방법 중 하나. 한 번 구한 결과를 메모리 공간에 메모해두고 같은 식을 다시 호출하면 메모한 결과를 그대로 가져오는 기법, `캐싱`이라고도 함

```python
# 한 번 계산된 결과를 메모이제이션하기 위한 리스트 초기화
d = [0] * 100

# 피보나치 함수를 재귀 함수로 구현(탑다운 다이나믹 프로그래밍)
def fibo(x):
    # 종료 조건(1 혹은 2일 때 1을 반환)
    if x == 1 or x == 2:
        return 1
    # 이미 계산한 적 있는 문제라면 그대로 반환
    if d[x] != 0:
        return d[x]
    # 아직 계산하지 않은 문제라면 점화식에 따라서 피보나치 결과 반환
    d[x] = fibo(x - 1) + fibo(x - 2)
    return d[x]

print(fibo(99))
```