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
