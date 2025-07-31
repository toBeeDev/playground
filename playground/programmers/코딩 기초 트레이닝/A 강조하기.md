## 문제 설명

문자열 `myString`이 주어집니다.  
`myString`에서 알파벳 "a"가 등장하면 전부 "A"로 변환하고,  
"A"가 아닌 모든 대문자 알파벳은 소문자 알파벳으로 변환하여 return 하는 solution 함수를 완성하세요.

---

## 제한사항

- 1 ≤ myString의 길이 ≤ 20
- myString은 알파벳으로 이루어진 문자열입니다.

---

## 입출력 예

| myString           | result             |
| ------------------ | ------------------ |
| "abstract algebra" | "AbstrAct AlgebrA" |
| "PrOgRaMmErS"      | "progrAmmers"      |

---

## 입출력 예 설명

### 입출력 예 #1

- 0번, 5번, 9번, 15번 인덱스의 "a"는 소문자이므로 전부 대문자로 고쳐줍니다.
- 다른 문자들은 전부 "a"가 아닌 소문자이므로 바꾸지 않습니다.
- 따라서 "AbstrAct AlgebrA"를 return 합니다.

### 입출력 예 #2

- 0번, 2번, 4번, 6번, 8번, 10번 인덱스의 문자들은 "A"가 아닌 대문자이므로 전부 소문자로 고쳐줍니다.
- 5번 인덱스의 "a"는 소문자이므로 대문자로 고쳐줍니다.
- 다른 문자들은 전부 "a"가 아닌 소문자이므로 바꾸지 않습니다.
- 따라서 "progrAmmers"를 return 합니다.

---

## 풀이 코드

```javascript
function solution(myString) {
  return myString.toLowerCase().replaceAll("a", "A");
}
```

---

## 고민한 점

- 문자열을 먼저 모두 소문자로 변환한 후, "a"를 "A"로 바꾸는 순서가 중요함을 고민했습니다.
- `toLowerCase()`와 `replaceAll()`을 조합해 간결하게 해결할 수 있었습니다.

---

## 더 알아본 점

- JavaScript에서 `toLowerCase()`를 사용해 모든 문자를 소문자로 변환하는 방법을 복습했습니다.
- `replaceAll()`을 사용해 특정 문자를 모두 다른 문자로 바꾸는 방법을 다시 확인했습니다.
