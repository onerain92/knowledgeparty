---
description: >-
  문제 난이도: 중 / 문제 유형 : 스택, 구현, 그리디 / 풀이 시간 : 40분 /
  https://www.acmicpc.net/problem/5397
---

# 키로거

## 1. 문제 풀이 핵심 아이디어

* 문자열 크기가 최대 1,000,000 이므로 시뮬레이션 방식으로 문제를 해결할 수 없다.
* 스택을 활용하여 선형시간 문제를 해결할 수 있는 알고리즘을 설계해야 한다.

1. 스택 두 개를 만들고, 스택 두 개의 중간 지점을 커서\( Cursor \)로 간주한다.
2. 문자 입력 : 왼쪽 스택에 원소를 삽입한다.
3. ' - ' 입력 : 왼쪽 스택에서 원소를 삭제한다.
4. &lt; 입력 : 왼쪽 스택에서 오른쪽 스택으로 원소를 이동시킨다.
5. &gt; 입력 : 오른쪽 스택에서 왼쪽 스택으로 원소를 이동시킨다.

```text
def solution(key_input):
    answer = []
    temp = []

    for key in key_input:
        if key == '<':
            if answer:
                temp.append(answer.pop())
        elif key == '>':
            if temp:
                answer.append(temp.pop())
        elif key == '-':
            if answer:
                answer.pop()
        else:
            answer.append(key)

    for _ in range(len(temp)):
        answer.append(temp.pop())

    return ''.join(answer)


print(solution('<<BP<A>>Cd-'))
print(solution('ThIsIsS3Cr3t'))
print(solution('ABC<<D>E<<F>>--'))
```

```text
def solution2():
    test_case = int(input())

    for _ in range(test_case):
        left_stack = []
        right_stack = []
        key_input = input()

        for key in key_input:
            if key == '-':
                if left_stack:
                    left_stack.pop()
            elif key == '<':
                if left_stack:
                    right_stack.append(left_stack.pop())
            elif key == '>':
                if right_stack:
                    left_stack.append(right_stack.pop())
            else:
                left_stack.append(key)

    left_stack.extend(reversed(right_stack))

    return ''.join(left_stack)


print(solution2())
```

