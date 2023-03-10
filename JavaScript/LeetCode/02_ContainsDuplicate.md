## Problem ๐ฃ

Given an integer array nums, **return true** if any value appears at least twice in the array, and return false if every element is distinct.

```
Input: nums = [1,2,3,1]
Output: true
```

```
Input: nums = [1,2,3,4]
Output: false
```

<br>

## My Solution ๐

```jsx
const containsDuplicate = (nums) => {
  const arr = [];
  for (i in nums) {
    nums.filter((num) => num === nums[i]).length > 1 && arr.push(nums[i]);
  }
  return arr.length > 0 && true;
};
```

`filter`๋ฅผ ์ฌ์ฉํด์ nums์ ๋ค์ด์๋ ์์๋ค์ ์ค๋ณต์ ํ์ธํ๊ณ , ๊ทธ ๊ธธ์ด๊ฐ 1์ด ๋์ผ๋ฉด (= ์ค๋ณต์ด ์์ผ๋ฉด) ๋น ๋ฐฐ์ด์ธ `arr`์ ์์๋ฅผ ๋ฃ์๋ค. ๋ง์ง๋ง์ผ๋ก arr.length ํ์ธ์ ํตํด ์ค๋ณต์ธ ๊ฒฝ์ฐ **true**๋ฅผ ๋ฐํ ํ๊ฒ ๋๋ค.

<br>

ใฐ๏ธ ์๊ฐ์ด ์ค๋ ๊ฑธ๋ ค ์ ๋ต ํ์ธ์ด ์ด๋ ค์ ์...

<br>

## Solution ๐ฌ

```jsx
var containsDuplicate = function (nums) {
  const set = new Set([...nums]);
  return set.size != nums.length;
};
```

์๋ฐ์คํฌ๋ฆฝํธ์์ `Set` ๊ฐ์ฒด๋ ์ค๋ณต๋์ง ์๋ ์ ์ผํ ๊ฐ๋ค์ ์งํฉ์ ๋ปํ๋ค. ๋ฐฐ์ด์ธ nums๋ฅผ ์ค๋ณต๋์ง ์๋ ๊ฐ๋ค๋ก ๋์ดํ๊ธฐ ์ํด `set`์ผ๋ก ๋ณ๊ฒฝํ๊ฒ ๋๋ค. ์ดํ, ์๋ณธ(nums)์ ๊ธธ์ด์ ์ค๋ณต์ ์ ์ธํ ๊ฐ๋ค์ ์งํฉ์ ๊ธธ์ด๋ฅผ ๋น๊ตํด ๊ทธ ๊ฒฐ๊ณผ๋ฅผ return ํ๊ฒ ๋๋ค.

โ set ๊ฐ์ฒด๋ ์ค๋ณต์ ํ์ฉํ์ง ์๋๋ค. `new Set()` ์์ฑ์๋ฅผ ํตํด ์ค๋ณต๊ฐ์ ์ ๊ฑฐ
<br>
โ `set๊ฐ์ฒด.size` ์์์ ๊ฐ์๋ฅผ ํ์ธํ  ์ ์๋ค.

---

<br>

## ์ฐธ๊ณ ์๋ฃ ๐

- https://velog.io/@dolarge/Java-Script-Set-%EA%B3%BC-Map
- https://relatablecode.com/javascript-leetcode-contains-duplicate
