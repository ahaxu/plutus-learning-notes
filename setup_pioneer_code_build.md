### Setup Pioneer Program environment

__this guider is noted by [https://twitter.com/DangQuanNguyen](https://twitter.com/DangQuanNguyen)__

0. Prerequisites

Set up Plutus & Plutus Playground: see README.md

1. Clone Pioneer repo

```
git clone https://github.com/lsmor/plutus-pioneer-program.git
```

2. Build pioneer code

Go to your plutus root folder (not the pioneer code folder), see prerequisites:

```
cd plutus
nix-shell
```

Go to your pioneer code folder:

```
cd plutus-pioneer-program/code/week01
cabal new-build
```

3. Run code

Copy the code from src/Week01/EnglishAuction.hs to the plutus code editor at https://localhost:8009 (see prerequisites)
Remove the 'module' declaration (lines 18-30)
Compile the code and simulate it.
See Lars' video at https://www.youtube.com/watch?v=IEn6jUo-0vU

4. For the future weeks

You just need to go to the plutus-pioneer-program folder and do a

```
git pull
```
to update the code. Then run

```
cabal build
```
to rebuild the code. Then you should be able to copy the code over to the plutus-playground editor and test it there.
