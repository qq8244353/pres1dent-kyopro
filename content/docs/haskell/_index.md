---
title: haskellまとめ
type: docs
---
# 入力
```haskell
getInt :: IO Int
getInt = fst . fromJust . BS.readInt <$> BS.getLine

getInts :: IO [Int]
getInts = unfoldr (BS.readInt . BS.dropWhile isSpace) <$> BS.getLine
```
# 重複除去
`ord`はO(N^2). 順序が定義されている場合, O(nlogn)の`nubOrd`を利用できる.
