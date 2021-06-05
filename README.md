https://github.com/commercialhaskell/stack/issues/4428

Repro: `stack haddock`

Running this with `-v` shows it erroring with the following command:
```
~/.stack/setup-exe-cache/x86_64-osx/Cabal-simple_mPHDZzAJ_3.2.1.0_ghc-8.10.4 --builddir=.stack-work/dist/x86_64-osx/Cabal-3.2.1.0 haddock --html --hoogle --html-location=../$pkg-$version/ --haddock-option=--hyperlinked-source --haddock-option=--quickjump
```

The bug still occurs when using GHC 9.0.1, which uses Cabal 3.4.0.0. But doing `cabal haddock` with Cabal 3.4.0.0 works.

Digging deeper, it seems like this could be a bug in Cabal-the-library. The following steps should also error:

```bash
export PATH=~/.stack/programs/x86_64-osx/ghc-9.0.1/bin:$PATH
ghc -package Cabal-3.4.0.0 Setup.hs -o setup
./setup configure
./setup haddock
```
