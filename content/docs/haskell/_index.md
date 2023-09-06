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
# Not Equal
/= (equal は ==)
# <$> と <*>
<$> は fmap の略. <*> は <$> の引数が複数ある時に繋げるために使う.
```haskell
ghci> (*2) <$> [1..3]
[2,4,6]
ghci> (*) <$> [1 .. 3] <*> [11 .. 13]
[11,12,13,22,24,26,33,36,39]
```
2個目の挙動はいまいちよくわかってない
# listの結合
```haskell
ghci> [1..2] ++ [3..4]
[1,2,3,4]
```
# flatten
```haskell
ghci> concat [[1,2],[3,4]]
[1,2,3,4]
```
# replicateM n
`replicateM n` でn回アクションをおこなって、結果を配列に入れて返す.
(Mはモナドのこと)
例:
```haskell
input1 <- replicateM n getInts
input2 <- replicateM n do
    [u, v] <- getInts
    // dosomething
    return (something)
```


