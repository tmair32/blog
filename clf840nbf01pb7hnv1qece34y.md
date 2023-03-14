---
title: "[6kyu] Multiplication table"
seoTitle: "Multiplication table"
seoDescription: "Here is a solution to the 6kyu-level Codewars problem "Multiplication table?."
datePublished: Tue Mar 14 2023 10:27:39 GMT+0000 (Coordinated Universal Time)
cuid: clf840nbf01pb7hnv1qece34y
slug: multiplication-table
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1678778944604/734573f3-66a5-4937-9340-7e36d7556a73.webp
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1678779083151/f036e3c1-fbaf-4829-9c6e-5bd60d2f1646.webp
tags: algorithms, javascript, typescript, codewars, 6kyu

---

## Instructions

Your task, is to create N×N multiplication table, of size provided in parameter.

For example, when given `size` is 3:

```typescript
1 2 3
2 4 6
3 6 9
```

For the given example, the return value should be:

```typescript
[[1,2,3],[2,4,6],[3,6,9]]
```

---

## My solution

```typescript
export function multiplicationTable (size: number): number[][] {
  return Array.from({length: size}, (_, i) => Array.from({length: size}, (_, j) => (i + 1) * (j + 1)));
}
```

Please check this problem at this [Link](https://www.codewars.com/kata/534d2f5b5371ecf8d2000a08/train/typescript)!