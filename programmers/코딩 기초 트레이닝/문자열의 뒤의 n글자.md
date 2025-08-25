# 문자열의 뒤의 n글자

## 문제 설명

문자열 `my_string`과 정수 `n`이 매개변수로 주어질 때, `my_string`의 뒤의 n글자로 이루어진 문자열을 return 하는 solution 함수를 작성해 주세요.

**제한사항:**

- `my_string`은 숫자와 알파벳으로 이루어져 있습니다.
- 1 ≤ `my_string`의 길이 ≤ 1,000
- 1 ≤ n ≤ `my_string`의 길이

**입출력 예:**
| my_string | n | result |
|-----------|---|--------|
| "ProgrammerS123" | 11 | "grammerS123" |
| "He110W0r1d" | 5 | "W0r1d" |

## 해결 방법

```javascript
function solution(my_string, n) {
  const a = my_string.length - n;
  return my_string.slice(a);
}
```

**개선된 코드:**

```javascript
function solution(my_string, n) {
  return my_string.slice(-n);
}
```

## 고민한 점

1. **문자열 자르기 방법**: 처음에는 문자열의 길이에서 n을 빼서 시작 인덱스를 구한 후 `slice()`를 사용했습니다.

2. **음수 인덱스 활용**: JavaScript의 `slice()` 메서드는 음수 인덱스를 지원하므로, `slice(-n)`을 사용하면 뒤에서부터 n개의 문자를 더 간단하게 추출할 수 있습니다.

3. **가독성 향상**: 개선된 코드는 더 직관적이고 간결하며, 의도를 명확하게 표현합니다.
