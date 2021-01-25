# Consensus - Emscripten

Small library for multiple parties to estbalish a shared random number. Even if you are the only honest party.

Inclues a webassembly/javascript compiled version of [libtomcrypt](https://github.com/libtom/libtomcrypt).

**This version is not necessarily compatible with [consensus](https://github.com/ali-raheem/consensus) or [consensus-sodium](https://github.com/ali-raheem/consensus-sodium) but all now use the blake2b-256 hash.**

## Algorithim

1. All parties pick a secret random number
2. Each party shares a hash of that random number
3. Each party reveals the random number
4. Each party ensures the hashes matches the revealed number
5. All the random numbers are bitwise XOR'd to produce a random number

## Dependencies

- [libtomcrypt](https://github.com/libtom/libtomcrypt) due to extreme portability
- Emscripten

## Build

```
emcc src/test.c src/consensus.c lib/libtomcrypt.a -I include/ -o bin/test.html
```

## Usage

See `src/test.c`, each party only generates one secret, disseminating the hash, and then the secret is left up to the user. For most applications you will want to process the secret for example hasing it.