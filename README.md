https://github.com/commercialhaskell/stack/issues/4428

# Stack repro

Repro: `stack haddock`

Running this with `-v` shows it erroring with the following command:
```
~/.stack/setup-exe-cache/x86_64-osx/Cabal-simple_mPHDZzAJ_3.2.1.0_ghc-8.10.4 --builddir=.stack-work/dist/x86_64-osx/Cabal-3.2.1.0 haddock --html --hoogle --html-location=../$pkg-$version/ --haddock-option=--hyperlinked-source --haddock-option=--quickjump
```

# GHC repro

```
ghc configure
ghc haddock
```
