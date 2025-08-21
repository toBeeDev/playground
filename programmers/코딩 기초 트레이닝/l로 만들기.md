# l로 만들기

## 문제 설명

알파벳 소문자로 이루어진 문자열 myString이 주어집니다. 알파벳 순서에서 "l"보다 앞서는 모든 문자를 "l"로 바꾼 문자열을 return 하는 solution 함수를 완성해 주세요.

**제한사항**

- 1 ≤ myString ≤ 100,000
- myString은 알파벳 소문자로 이루어진 문자열입니다.

**입출력 예**
| myString | result |
|----------|--------|
| "abcdevwxyz" | "lllllvwxyz" |
| "jjnnllkkmm" | "llnnllllmm" |

## 해결 코드

```javascript
// 기본 해결 방법
function solution(myString) {
  const test = myString.split("");
  const regex = /[a-k]/;
  const a = test.map((item, idx) => (regex.test(item) ? "l" : item));
  return a.join("");
}

// 개선된 해결 방법
function solution(myString) {
  return myString.replace(/[a-k]/g, "l");
}
```

## 고민한 점

1. **문자 비교 방법**: 'l'보다 앞선 문자들을 찾는 방법으로 정규식 `[a-k]`를 사용하는 것이 효율적이었습니다.

2. **성능 최적화**: 기존 코드는 `split()` → `map()` → `join()` 단계를 거치지만, 개선된 코드는 `replace()` 한 번으로 처리하여 더 간결하고 효율적입니다.

3. **정규식 플래그**: 전역 플래그 `g`를 사용하여 모든 일치하는 문자를 한 번에 변경할 수 있습니다.

4. **문자 범위**: 알파벳 순서에서 'l'보다 앞선 문자는 'a'부터 'k'까지이므로 `[a-k]` 패턴을 사용했습니다.
