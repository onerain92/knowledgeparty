---
description: '데이터를 나열하고, 각 데이터를 인덱스에 대응하도록 구성한 데이터 구조'
---

# 배열

## 배열이 왜 필요할까?

* 같은 종류의 데이터를 효율적으로 관리하기 위해 사용.
* 같은 종류의 데이터를 순차적으로 저장.

![](.gitbook/assets/img_0255.jpg)

### 배열의 장점

* 빠른 접근 가능.

### 배열의 단점

* 추가 / 삭제가 쉽지 않음.
* 미리 최대 길이를 지정해야 함.



## 파이썬과 C언어의 배열 예제

### C언어

```text
#include<stdio.h>

int main(int argc, char* argv[]) {
    char country[3] = "US";
    printf("%c%c\n", country[0], country[1]);
    printf("%s\n", country);
    return 0;
}
```

* 지정한 3자리 이외에 데이터를 더 넣으려면 변수를 재지정해야함.

### Python

```text
country = "US"
print(country) // US

country = country + 'A'
print(country) // USA
```



## 배열 \( Python \)

### 1차원 배

```text
data = [1, 2, 3, 4, 5]

print(data) // [1, 2, 3, 4, 5]
```

### 2차원 배열

```text
data = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]

print(data) // [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
print(data[0] // [1, 2, 3]
print(data[0][0]) // 1
print(data[0][1]) // 2
print(data[0][2]) // 3
print(data[1][0]) // 4
```



## 연습

1, 2차원 배열에서 9, 8, 7 순서로 출력해보.

```text
data = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]

print(data[2][2], data[2][1], data[2][0]) // 9, 8, 7
```

2. 다음 dataset에서 전체 이름 안에 M이 몇 번 나왔는지 빈도수 체크하기.

```text
dataset = [
'Braund', 'Mr.Owen Harris', 'Cumings', 
'Mrs.John Bradley(Florence Briggs Thayer)',
'Heikkinen', 'Miss.Laina', 'Futrelle',
'Mrs.Jacques Heath(Lily May Peel)',
'Allen', 'Mr.Willam Henry', 'Moran, Mr.James',
'McCarthy, Mr.Timothy J'
]

m_count = 0
for data in dataset:
    for index in range(len(data)):
        if data[index] == 'M':
            m_count += 1

print(m_count)
```



