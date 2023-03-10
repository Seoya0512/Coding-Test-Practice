## Problem ๐ฃ

Given an array of strings strs, group the anagrams together. You can return the answer in any order.

An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

```
Input: ["eat", "tea", "tan", "ate", "nat", "bat"],
Output:
[
  ["ate","eat","tea"],
  ["nat","tan"],
  ["bat"]
]
```

<br>

## My Solution ๐

๋๊ธฐ๋ค๊ณผ ํจ๊ป ํ์ ๋ต๋ณ..

```jsx
const groupAnagrams = (strs) => {
  const arr = [
    ...new Set(
      strs.map((str) => {
        return str.split("").sort().join("");
      })
    ),
  ];
  const result = [];
  for (let i of arr) {
    let a = [];
    for (let str of strs) {
      if (i === str.split("").sort().join("")) {
        a.push(str);
      }
    }
    result.push(a);
  }
  return result;
};
```

`arr`๋ strs์ ์๋ ์์๋ค์ ์์๋๋ก ์ ๋ ฌํ ํ ์ค๋ณต๋์ง ์๋๋ก ๋ง๋  ๋ฐฐ์ด์ด๋ค. ์ดํ, arr์ ์์๋ค๊ณผ strs(์๋ ๋ฐฐ์ด)์ ๋ค์ด ์๋ ์์๋ค์ ๋น๊ตํ๋ฉฐ ๊ฐ์ ๊ฒฝ์ฐ ๋ฐฐ์ด `a`์ push ํ๊ฒ ๋๋ค. ๋ง์ง๋ง์ผ๋ก ๋ง๋ค์ด์ง ๋ฐฐ์ด `a`๋ฅผ ์ ์ฒด `result` ๋ฐฐ์ด์ ํ ๋ฒ ๋ push ํจ์ผ๋ก ์ํ๋ ๊ฒฐ๊ณผ๊ฐ์ ์ป์ ์ ์๋ค.

<br>

ใฐ๏ธ ์๊ฐ์ด ์ค๋ ๊ฑธ๋ ค ์ ๋ต ํ์ธ์ด ์ด๋ ค์ ์... (111/120 passed)

<br>

## Solution ๐ฌ

```jsx
const groupAnagrams = (strs) => {
  const mapping = {};
  for (let str of strs) {
    const sorted = str.split("").sort().join("");
    if (mapping[sorted] !== undefined) {
      mapping[sorted].push(str);
    } else {
      mapping[sorted] = [str];
    }
  }
  return Object.values(mapping);
};
```

Object์ ์ฑ์ง์ ํ์ฉํด์ ํ์ดํ ๋ด์ฉ์ด๋ค. ๋จผ์  strs์ ์์๋ฅผ ์์๋๋ก ์ ๋ ฌํ (sorted)๋ฅผ `mapping` Object์ key ๊ฐ์ผ๋ก ์ง์ ํ๋ค. ์ดํ, ํค ๊ฐ์ value๊ฐ ์กด์ฌํ๋ฉด, ๊ทธ ๋ฐฐ์ด(๊ฐ)์ push ํ๊ณ , ์๋ ๊ฒฝ์ฐ ๋ฐฐ์ด๋ก๋ value๋ฅผ ๋ง๋ค์ด ์ฃผ๊ฒ ๋๋ค. ์ดํ, Object์ `value` ๋ง ๊ฐ์ ธ์ค๊ฒ ๋๋ฉด, ์ฐ๋ฆฌ๊ฐ ์ํ๋ ๊ฐ์ ๊ฐ์ง ์ ์๋ค.

<br>

โ Object์ key-value๋ฅผ ์ฌ์ฉํด ๊ฐ์ ์ ์ํ๊ณ  ๋น๊ตํ๊ณ  ์ฐพ์ ์ ์๋ค. ๋ณต์กํ for loop ๋ฑ์ ๋ฐ๋ณต๋ฌธ์ ์ฌ์ฉํ์ง ์์๋ ๋๋ค.

---

<br>

## ์ฐธ๊ณ ์๋ฃ ๐

- https://leetcode.com/problems/group-anagrams/solutions/19441/simple-javascript-solution/?languageTags=javascript
