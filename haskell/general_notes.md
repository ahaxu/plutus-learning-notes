## Basic stuff 

 - Datatypes: type constructor & data constructor
 - Pattern matching
 - Folding


## Functor

Laws
    - todo

fmap :: Functor f => (a -> b) -> f a -> f b
map
(.)
($)
(->)

## Applicative
Laws
    - todo

Minimal function need to implement:
```
pure
<*>
```

```
Student <$> firstname <*> lastname
liftA2 Student firstname lastname
```

## Monad
Laws
    - todo

Minimal function need to implement:
```
return
>>= :: join fmap
=<< :: flip (>>=)
```

Maybe Monad -- computation can be fail
Either Monad -- exception handler
(->) and Reader Monad -- waiting for input from env
State Monad -- memoize data
Writer Monad 

## Compose
Compose f g a
Functor 
Applicative
Monad

## Monad transformer

#### Why we need monad transformers

Because monad can't compose

```
f g ( f (g b)) --> f (g b) --> join fmap ??
```
Only if we have a function like on swap :: m (n s) --> n (m s)

Refer document: http://web.cecs.pdx.edu/~mpj/pubs/RR-1004.pdf

#### Common Monad transformers

- IndentityT
- MaybeT
- ReaderT
- EitherT
- StateT

#### Videos and article

- [Adam McCullough - Monad Transformers for the Easily Confused - λC 2018](https://www.youtube.com/watch?v=SMj-n2f7wYY&t=1583s)
- [Monad Transformers - Ben Kolera](https://www.youtube.com/watch?v=pzouxmWiemg)
- [mmhaskell monads transformers](https://mmhaskell.com/monads/transformers)

