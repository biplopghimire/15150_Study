## Higher Order Functions (HOFs)

### `map`

```sml
(* map : (‘a -> ‘b) -> ‘a list -> ‘b list *)
fun map f [] = []
  | map f (x::xs) = f x :: map f xs
```

### foldl (Left Fold)

```sml
(* foldl : (‘a * ‘b -> ‘b) -> ‘b -> ‘a list -> ‘b *)
fun foldl f z [] = z
  | foldl f z (x::xs) = foldl f (f(x, z)) xs
```

### foldr (Right Fold)

```sml
(* foldr : (‘a * ‘b -> ‘b) -> ‘b -> ‘a list -> ‘b *)
fun foldr f z [] = z
  | foldr f z (x::xs) = f(x, foldr f z xs)
```
