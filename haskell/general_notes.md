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

pure
<****>
f <$> Student <*> firstname <*> lastname

## Monad
Laws
    - todo

return
>>= :: join fmap
=<< :: flip (>>=)

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

Because monad can't compose
f g ( f (g b)) --> f (g b) --> join fmap ??

only if we have a function like on swap :: m (n s) --> n (m s)

refer document: http://web.cecs.pdx.edu/~mpj/pubs/RR-1004.pdf

IndentityT
MaybeT
ReaderT
EitherT
StateT

Videos and article
    - [Adam McCullough - Monad Transformers for the Easily Confused - λC 2018](https://www.youtube.com/watch?v=SMj-n2f7wYY&t=1583s)
    - [Monad Transformers - Ben Kolera](https://www.youtube.com/watch?v=pzouxmWiemg)
    - [mmhaskell monads transformers](https://mmhaskell.com/monads/transformers)
