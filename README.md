# nanoKeyManager
A go module to generate or manipulate addresses for the crytpocurrenty [nano](https://nano.org).

Features:
- Can generate cryptographically safe addresses
- Can derive public addresses and their ascii counterparts
- Can translate seeds to/from bip39 mnemonics
- Can derive any address from its seed and index

## Examples

Generate a new seed
```go
var seed nanoKeyManger.Key

// Generates a new seed. Defaults to index 0.
nanoKeyManger.GenerateSeed(&seed)
// Print address of index 0.
fmt.Println(seed)
```


Derive keys with a given seed
```go
var seed nanoKeyManger.Key
seed.Seed = userInputSeed
seed.Index = userInputIndex

// Derive public keys based on seed/index
nanoKeyManager.SeedToKeys(&seed)
fmt.Println(seed)
```

Derive public key from ascii address
```go
var nanoAddress string
var pubKey []byte
var err error

nanoAddress = userAddress

pubKey, err = nanoKeyManager.AddressToPubKey(nanoAddress)
if (err != nil) {
  // Handle error
}

// Now go in reverse
var reDerivedAddress string

reDerivedAddress, err = nanoKeyManager.PubKeyToAddress(pubKey)
if (err != nil) {
  // Handle error
}

// reDerivedAddress == nanoAddress
```
---

For further reading examine [seeds.go](https://github.com/Tumbler/nanoKeyManager/blob/main/seeds.go)
