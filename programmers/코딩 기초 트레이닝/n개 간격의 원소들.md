# n개 간격의 원소들

## 문제 설명

정수 리스트 `num_list`와 정수 `n`이 주어질 때, `num_list`의 첫 번째 원소부터 마지막 원소까지 `n`개 간격으로 저장되어있는 원소들을 차례로 담은 리스트를 return하도록 solution 함수를 완성해주세요.

### 제한사항

- 5 ≤ num_list의 길이 ≤ 20
- 1 ≤ num_list의 원소 ≤ 9
- 1 ≤ n ≤ 4

### 입출력 예

| num_list           | n   | result    |
| ------------------ | --- | --------- |
| [4, 2, 6, 1, 7, 6] | 2   | [4, 6, 7] |
| [4, 2, 6, 1, 7, 6] | 4   | [4, 7]    |

## 해결 방법

### 기본 해법

```javascript
function solution(num_list, n) {
  return num_list.filter((item, index) => index % n === 0);
}
```

### 개선된 해법

```javascript
function solution(num_list, n) {
  const result = [];
  for (let i = 0; i < num_list.length; i += n) {
    result.push(num_list[i]);
  }
  return result;
}

// 또는 슬라이싱을 활용한 방법
function solution(num_list, n) {
  return num_list.filter((_, index) => index % n === 0);
}
```

## 고민한 점

1. **인덱스 기반 접근**: n개 간격이라는 것은 인덱스 0부터 시작해서 n씩 증가하는 위치의 원소들을 선택하는 것입니다.

2. **filter vs for loop**:

   - `filter` 방법은 모든 원소를 순회하면서 조건을 체크합니다
   - `for loop` 방법은 필요한 인덱스만 방문하므로 더 효율적입니다

3. **모듈러 연산 활용**: `index % n === 0` 조건으로 n의 배수 인덱스만 선택할 수 있습니다.

4. **가독성**: filter 메소드가 함수형 프로그래밍 스타일로 더 직관적이고 간결합니다.
