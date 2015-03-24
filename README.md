# Module Documentation

## Module Data.Tuple

#### `Tuple`

``` purescript
data Tuple a b
  = Tuple a b
```

A simple product type for wrapping a pair of component values.

#### `showTuple`

``` purescript
instance showTuple :: (Show a, Show b) => Show (Tuple a b)
```

Allows `Tuple`s to be rendered as a string with `show` whenever there are
`Show` instances for both component types.

#### `eqTuple`

``` purescript
instance eqTuple :: (Eq a, Eq b) => Eq (Tuple a b)
```

Allows `Tuple`s to be checked for equality with `==` and `/=` whenever
there are `Eq` instances for both component types.

#### `ordTuple`

``` purescript
instance ordTuple :: (Ord a, Ord b) => Ord (Tuple a b)
```

Allows `Tuple`s to be compared with `compare`, `>`, `>=`, `<` and `<=`
whenever there are `Ord` instances for both component types. To obtain
the result, the `fst`s are `compare`d, and if they are `EQ`ual, the
`snd`s are `compare`d.

#### `semigroupoidTuple`

``` purescript
instance semigroupoidTuple :: Semigroupoid Tuple
```


#### `semigroupTuple`

``` purescript
instance semigroupTuple :: (Semigroup a, Semigroup b) => Semigroup (Tuple a b)
```

The `Semigroup` instance enables use of the associative operator `<>` on
`Tuple`s whenever there are `Semigroup` instances for the component
types. The `<>` operator is applied pairwise, so:
```purescript
(Tuple a1 b1) <> (Tuple a2 b2) = Tuple (a1 <> a2) (b1 <> b2)
```

#### `monoidTuple`

``` purescript
instance monoidTuple :: (Monoid a, Monoid b) => Monoid (Tuple a b)
```


#### `functorTuple`

``` purescript
instance functorTuple :: Functor (Tuple a)
```

The `Functor` instance allows functions to transform the contents of a
`Tuple` with the `<$>` operator, applying the function to the second
component, so:
```purescript
f <$> (Tuple x y) = Tuple x (f y)
````

#### `applyTuple`

``` purescript
instance applyTuple :: (Semigroup a) => Apply (Tuple a)
```

The `Functor` instance allows functions to transform the contents of a
`Tuple` with the `<*>` operator whenever there is a `Semigroup` instance
for the `fst` component, so:
```purescript
(Tuple a1 f) <*> (Tuple a2 x) == Tuple (a1 <> a2) (f x)
```

#### `applicativeTuple`

``` purescript
instance applicativeTuple :: (Monoid a) => Applicative (Tuple a)
```


#### `bindTuple`

``` purescript
instance bindTuple :: (Semigroup a) => Bind (Tuple a)
```


#### `monadTuple`

``` purescript
instance monadTuple :: (Monoid a) => Monad (Tuple a)
```


#### `extendTuple`

``` purescript
instance extendTuple :: Extend (Tuple a)
```


#### `comonadTuple`

``` purescript
instance comonadTuple :: Comonad (Tuple a)
```


#### `lazyTuple`

``` purescript
instance lazyTuple :: (Lazy a, Lazy b) => Lazy (Tuple a b)
```


#### `lazyLazy1Tuple`

``` purescript
instance lazyLazy1Tuple :: (Lazy1 l1, Lazy1 l2) => Lazy (Tuple (l1 a) (l2 b))
```


#### `lazyLazy2Tuple`

``` purescript
instance lazyLazy2Tuple :: (Lazy2 l1, Lazy2 l2) => Lazy (Tuple (l1 a b) (l2 c d))
```


#### `fst`

``` purescript
fst :: forall a b. Tuple a b -> a
```

Returns the first component of a tuple.

#### `snd`

``` purescript
snd :: forall a b. Tuple a b -> b
```

Returns the second component of a tuple.

#### `curry`

``` purescript
curry :: forall a b c. (Tuple a b -> c) -> a -> b -> c
```

Turn a function that expects a tuple into a function of two arguments.

#### `uncurry`

``` purescript
uncurry :: forall a b c. (a -> b -> c) -> Tuple a b -> c
```

Turn a function of two arguments into a function that expects a tuple.

#### `zip`

``` purescript
zip :: forall a b. [a] -> [b] -> [Tuple a b]
```

Rakes two lists and returns a list of corresponding pairs.
If one input list is short, excess elements of the longer list are discarded.

#### `unzip`

``` purescript
unzip :: forall a b. [Tuple a b] -> Tuple [a] [b]
```

Transforms a list of pairs into a list of first components and a list of
second components.

#### `swap`

``` purescript
swap :: forall a b. Tuple a b -> Tuple b a
```

Exchange the first and second components of a tuple.


## Module Data.Tuple.Nested

#### `Tuple2`

``` purescript
type Tuple2 a z = Tuple a z
```


#### `Tuple3`

``` purescript
type Tuple3 a b z = Tuple (Tuple2 a b) z
```


#### `Tuple4`

``` purescript
type Tuple4 a b c z = Tuple (Tuple3 a b c) z
```


#### `Tuple5`

``` purescript
type Tuple5 a b c d z = Tuple (Tuple4 a b c d) z
```


#### `Tuple6`

``` purescript
type Tuple6 a b c d e z = Tuple (Tuple5 a b c d e) z
```


#### `Tuple7`

``` purescript
type Tuple7 a b c d e f z = Tuple (Tuple6 a b c d e f) z
```


#### `Tuple8`

``` purescript
type Tuple8 a b c d e f g z = Tuple (Tuple7 a b c d e f g) z
```


#### `Tuple9`

``` purescript
type Tuple9 a b c d e f g h z = Tuple (Tuple8 a b c d e f g h) z
```


#### `Tuple10`

``` purescript
type Tuple10 a b c d e f g h i z = Tuple (Tuple9 a b c d e f g h i) z
```


#### `tuple2`

``` purescript
tuple2 :: forall a b z. (a -> b -> z) -> Tuple2 a b -> z
```

Given a function of 2 arguments, return a function that accepts a 2-tuple.

#### `tuple3`

``` purescript
tuple3 :: forall a b c z. (a -> b -> c -> z) -> Tuple3 a b c -> z
```

Given a function of 3 arguments, return a function that accepts a 3-tuple.

#### `tuple4`

``` purescript
tuple4 :: forall a b c d z. (a -> b -> c -> d -> z) -> Tuple4 a b c d -> z
```

Given a function of 4 arguments, return a function that accepts a 4-tuple.

#### `tuple5`

``` purescript
tuple5 :: forall a b c d e z. (a -> b -> c -> d -> e -> z) -> Tuple5 a b c d e -> z
```

Given a function of 5 arguments, return a function that accepts a 5-tuple.

#### `tuple6`

``` purescript
tuple6 :: forall a b c d e f z. (a -> b -> c -> d -> e -> f -> z) -> Tuple6 a b c d e f -> z
```

Given a function of 6 arguments, return a function that accepts a 6-tuple.

#### `tuple7`

``` purescript
tuple7 :: forall a b c d e f g z. (a -> b -> c -> d -> e -> f -> g -> z) -> Tuple7 a b c d e f g -> z
```

Given a function of 7 arguments, return a function that accepts a 7-tuple.

#### `tuple8`

``` purescript
tuple8 :: forall a b c d e f g h z. (a -> b -> c -> d -> e -> f -> g -> h -> z) -> Tuple8 a b c d e f g h -> z
```

Given a function of 8 arguments, return a function that accepts a 8-tuple.

#### `tuple9`

``` purescript
tuple9 :: forall a b c d e f g h i z. (a -> b -> c -> d -> e -> f -> g -> h -> i -> z) -> Tuple9 a b c d e f g h i -> z
```

Given a function of 9 arguments, return a function that accepts a 9-tuple.

#### `tuple10`

``` purescript
tuple10 :: forall a b c d e f g h i j z. (a -> b -> c -> d -> e -> f -> g -> h -> i -> j -> z) -> Tuple10 a b c d e f g h i j -> z
```

Given a function of 10 arguments, return a function that accepts a 10-tuple.

#### `(/\)`

``` purescript
(/\) :: forall a b. a -> b -> Tuple a b
```

Shorthand for constructing n-tuples as nested pairs.
`a /\ b /\ c /\ d` becomes `Tuple (Tuple (Tuple a b) c ) d`