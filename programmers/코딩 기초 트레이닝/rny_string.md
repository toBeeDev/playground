# rny_string

## 문제 설명

'm'과 "rn"이 모양이 비슷하게 생긴 점을 활용해 문자열에 장난을 하려고 합니다. 문자열 rny_string이 주어질 때, rny_string의 모든 'm'을 "rn"으로 바꾼 문자열을 return 하는 solution 함수를 작성해 주세요.

**제한사항**

- 1 ≤ rny_string의 길이 ≤ 100
- rny_string은 영소문자로만 이루어져 있습니다.

**입출력 예**
| rny_string | result |
|---|---|
| "masterpiece" | "rnasterpiece" |
| "programmers" | "prograrnrners" |
| "jerry" | "jerry" |
| "burn" | "burn" |

## 해결방법

```javascript
function solution(rny_string) {
  return rny_string.replaceAll("m", "rn");
}
```

**개선된 버전 (다양한 접근법)**

```javascript
// 방법 1: replace + 정규표현식 사용
function solution(rny_string) {
  return rny_string.replace(/m/g, "rn");
}

// 방법 2: split + join 사용
function solution(rny_string) {
  return rny_string.split("m").join("rn");
}
```

## 고민한 점

- **문자열 치환 방법**: JavaScript에서 문자열의 모든 특정 문자를 치환하는 여러 방법이 있는데, `replaceAll()`이 가장 직관적이고 명확합니다.
- **성능 고려**: 문자열 길이가 최대 100이므로 성능상 큰 차이는 없지만, `replaceAll()`이 내부적으로 최적화되어 있어 가장 효율적입니다.
- **가독성**: 문제에서 "모든 'm'을 'rn'으로 바꾼다"고 명시되어 있어 `replaceAll('m', 'rn')`이 의도를 가장 명확하게 표현합니다.
