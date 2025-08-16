## 문제 설명 (제한사항 · 예시 포함)

문자열 `myString`이 주어집니다. `myString`을 문자 `"x"`를 기준으로 나눴을 때 나눠진 문자열 각각의 길이를 순서대로 저장한 배열을 return 하는 `solution` 함수를 완성해 주세요.

---

### 제한사항

- 1 ≤ `myString`의 길이 ≤ 100,000
- `myString`은 알파벳 소문자로 이루어진 문자열입니다.

---

### 입출력 예

| myString       | result             |
| -------------- | ------------------ |
| "oxooxoxxox"   | [1, 2, 1, 0, 1, 0] |
| "xabcxdefxghi" | [0, 3, 3, 3]       |

#### 입출력 예 설명

- 예시 1: `"x"`를 기준으로 나누면 ["o", "oo", "o", "", "o", ""] → 길이 [1, 2, 1, 0, 1, 0] 반환
- 예시 2: `"x"`를 기준으로 나누면 ["", "abc", "def", "ghi"] → 길이 [0, 3, 3, 3] 반환

---

## 풀이 코드 (개선 포함)

### 기본 풀이

```javascript
function solution(myString) {
  return myString.split("x").map((s) => s.length);
}
```

### 개선 풀이 (단일 패스, 추가 배열 최소화)

```javascript
function solution(myString) {
  const lengths = [];
  let runLength = 0;

  for (let i = 0; i < myString.length; i++) {
    if (myString[i] === "x") {
      lengths.push(runLength);
      runLength = 0;
    } else {
      runLength++;
    }
  }
  lengths.push(runLength);
  return lengths;
}
```

---

## 고민한 점

- 두 풀이 모두 시간 복잡도 O(n). 분리 배열 생성 비용을 줄이고 싶다면 단일 패스가 유리합니다.
- 시작/끝이 `"x"`이거나 `"x"`가 연속/존재하지 않는 경우까지 정상 동작합니다.
- 입력 길이가 최대 100,000으로 길 수 있어, 메모리 관점에서 개선 풀이가 유리할 수 있습니다.
