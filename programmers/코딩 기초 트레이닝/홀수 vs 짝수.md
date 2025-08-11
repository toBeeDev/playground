## 문제 설명 (제한사항 · 예시 포함)

정수 리스트 `num_list`가 주어집니다. 첫 번째 원소를 1번 원소라고 할 때, 홀수 번째 원소들의 합과 짝수 번째 원소들의 합 중 더 큰 값을 return 하도록 `solution` 함수를 완성하세요. 두 값이 같다면 그 값을 return 합니다.

---

### 제한사항

- 5 ≤ `num_list`의 길이 ≤ 50
- -9 ≤ `num_list`의 원소 ≤ 9

---

### 입출력 예

| num_list           | result |
| ------------------ | ------ |
| [4, 2, 6, 1, 7, 6] | 17     |
| [-1, 2, 5, 6, 3]   | 8      |

#### 입출력 예 설명

- 예시 1: 홀수 번째 합 = 4 + 6 + 7 = 17, 짝수 번째 합 = 2 + 1 + 6 = 9 → 17 반환
- 예시 2: 홀수 번째 합 = -1 + 5 + 3 = 7, 짝수 번째 합 = 2 + 6 = 8 → 8 반환

---

## 풀이 코드 (개선 포함)

### 기본 풀이 (filter + reduce)

```javascript
function solution(num_list) {
  const odd = num_list
    .filter((_, index) => index % 2 === 0)
    .reduce((a, b) => a + b, 0);
  const even = num_list
    .filter((_, index) => index % 2 !== 0)
    .reduce((a, b) => a + b, 0);

  return odd > even ? odd : even; // 같아도 그 값이 반환됨
}
```

### 개선 풀이 (한 번의 순회, 불필요한 배열 생성 제거)

```javascript
function solution(num_list) {
  let odd = 0; // 1-based 홀수 번째 → 0-based 인덱스가 짝수
  let even = 0; // 1-based 짝수 번째 → 0-based 인덱스가 홀수

  for (let i = 0; i < num_list.length; i += 1) {
    if (i % 2 === 0) odd += num_list[i];
    else even += num_list[i];
  }

  return Math.max(odd, even);
}
```

---

## 고민한 점

- 인덱스 기준이 1부터라는 조건을 JS의 0부터 시작하는 인덱스에 정확히 대응시키는 방법 (0-based 짝수 인덱스가 1-based 홀수 번째).
- `filter`로 부분 배열을 두 번 만드는 대신, 단일 순회로 합을 구하면 시간·공간 낭비를 줄일 수 있음.
- 원소에 음수가 포함되어도 합 비교 로직에는 영향이 없음을 확인.
