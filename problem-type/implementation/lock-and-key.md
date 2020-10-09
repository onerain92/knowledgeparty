---
description: >-
  문제 난이도: 중하 / 문제 풀이 시간 : 40분 / 시간 제한 : 1초 / 메모리 제한 : 128MB / 기출 : 2020 카카오 신입
  공채 / 링크 : https://programmers.co.kr/learn/courses/30/lessons/60059
---

# 5. 자물쇠와 열쇠

## 문제 설명

고고학자인 **튜브**는 고대 유적지에서 보물과 유적이 가득할 것으로 추정되는 비밀의 문을 발견하였습니다. 그런데 문을 열려고 살펴보니 특이한 형태의 **자물쇠**로 잠겨 있었고 문 앞에는 특이한 형태의 **열쇠**와 함께 자물쇠를 푸는 방법에 대해 다음과 같이 설명해 주는 종이가 발견되었습니다.

잠겨있는 자물쇠는 격자 한 칸의 크기가 **`1 x 1`**인 **`N x N`** 크기의 정사각 격자 형태이고 특이한 모양의 열쇠는 **`M x M`** 크기인 정사각 격자 형태로 되어 있습니다.

자물쇠에는 홈이 파여 있고 열쇠 또한 홈과 돌기 부분이 있습니다. 열쇠는 회전과 이동이 가능하며 열쇠의 돌기 부분을 자물쇠의 홈 부분에 딱 맞게 채우면 자물쇠가 열리게 되는 구조입니다. 자물쇠 영역을 벗어난 부분에 있는 열쇠의 홈과 돌기는 자물쇠를 여는 데 영향을 주지 않지만, 자물쇠 영역 내에서는 열쇠의 돌기 부분과 자물쇠의 홈 부분이 정확히 일치해야 하며 열쇠의 돌기와 자물쇠의 돌기가 만나서는 안됩니다. 또한 자물쇠의 모든 홈을 채워 비어있는 곳이 없어야 자물쇠를 열 수 있습니다.

열쇠를 나타내는 2차원 배열 key와 자물쇠를 나타내는 2차원 배열 lock이 매개변수로 주어질 때, 열쇠로 자물쇠를 열수 있으면 true를, 열 수 없으면 false를 return 하도록 solution 함수를 완성해주세요.



#### 제한사항

* key는 M x M\(3 ≤ M ≤ 20, M은 자연수\)크기 2차원 배열입니다.
* lock은 N x N\(3 ≤ N ≤ 20, N은 자연수\)크기 2차원 배열입니다.
* M은 항상 N 이하입니다.
* key와 lock의 원소는 0 또는 1로 이루어져 있습니다.
  * 0은 홈 부분, 1은 돌기 부분을 나타냅니다.

#### 입력 예시

| key | lock | result |
| :--- | :--- | :--- |
| \[\[0, 0, 0\], \[1, 0, 0\], \[0, 1, 1\]\] | \[\[1, 1, 1\], \[1, 1, 0\], \[1, 0, 1\]\] | true |



## 문제 해설

우리가 해야 할 일은 열쇠를 적당히 회전하고 이동시켜 자물쇠의 홈에 딱 맞게 끼워 넣는 것이다. 이 문제를 해결하기 위해서 얼마나 효율적인 알고리즘을 작성해야 하는지 고려해보자. 일단 문제에서 제시한 자물쇠와 열쇠의 크기는 20 x 20인 2차원 리스트에 있는 모든 원소에 접근할 때는 400만큼의 연산이 필요할 것이다. 파이썬의 경우 일반적인 코딩 테스트 채점 환경에서 1초에 2,000만에서 1억 정도의 연산을 처리할 수 있다. 그렇기 때문에 완전 탐색을 이용해서 열쇠를 이동이나 회전시켜서 자물쇠에 끼워보는 작업을 전부 시도해보는 접근 방법을 이용할 수 있다. 다시 말해 문제 해결 아이디어는 완전 탐색이다. 다만, 완전 탐색을 수월하게 하기 위해서 자물쇠 리스트의 크기를 3배 이상으로 변경하면 계산이 수월해진다.

## 답안

### 내가 푼 답안

```text
# 2차원 리스트 90도 회전
def rotate_a_matrix_by_90_degree(a):
    n = len(a) # 행 길이 계산
    m = len(a[0]) # 열 길이 계산
    result = [[0] * n for _ in range(m)] # 결과 리스트

    for i in range(n):
        for j in range(m):
            result[j][n - i - 1] = a[i][j]
    return result

# 자물쇠의 중간 부분이 모두 1인지 확인
def check(new_lock):
    lock_length = len(new_lock) // 3

    for i in range(lock_length, lock_length * 2):
        for j in range(lock_length, lock_length * 2):
            if new_lock[i][j] != 1:
                return False
    return True

def solution(key, lock):
    n = len(lock)
    m = len(key)

    # 자물쇠의 크기를 기존의 3배로 변환
    new_lock = [[0] * (n * 3) for _ in range(n * 3)]

    # 새로운 자물쇠의 중앙 부분에 기존의 자물쇠 넣기
    for i in range(n):
        for j in range(n):
            new_lock[i + n][j + n] = lock[i][j]

    # 4가지 방향에 대해서 확인
    for rotation in range(4):
        key = rotate_a_matrix_by_90_degree(key)
        for x in range(n * 2):
            for y  in range(n * 2):
                # 자물쇠에 열쇠를 끼워 넣기
                for i in range(m):
                    for j in range(m):
                        new_lock[x + i][y + j] += key[i][j]

                # 새로운 자물쇠에 열쇠가 정확히 들어맞는지 검사
                if check(new_lock) == True:
                    return True

                # 자물쇠에서 열쇠를 다시 빼기
                for i in range(m):
                    for j in range(m):
                        new_lock[x + i][y + j] -= key[i][j]

    return False


print(solution([[0, 0, 0], [1, 0, 0], [0, 1, 1]], [[1, 1, 1], [1, 1, 0], [1, 0, 1]]))

```



