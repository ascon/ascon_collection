Implementations of the Ascon Family
===================================

This is a collection of hardware and software implementations of Ascon.
Reference implementations are included as submodules, while this file lists additional implementations in various languages.

:warning: All repositories implement the submitted candidate design. The final NIST standard is not yet published and may be incompatible with these implementations due to minor changes.

:warning: Note that linked implementations may become outdated or incorrect and should not be used for productive environments without caution.


About Ascon
-----------

[Ascon](https://ascon.iaik.tugraz.at) is a family of [authenticated encryption](https://en.wikipedia.org/wiki/Authenticated_encryption) (AEAD) and [hashing](https://en.wikipedia.org/wiki/Cryptographic_hash_function) algorithms designed to be lightweight and easy to implement, even with added countermeasures against side-channel attacks.
It was designed by a team of cryptographers from Graz University of Technology, Infineon Technologies, and Intel Labs: Christoph Dobraunig, Maria Eichlseder, Florian Mendel, and Martin Schläffer.

Ascon has been selected as the standard for lightweight cryptography in the [NIST Lightweight Cryptography competition (2019–2023)](https://csrc.nist.gov/projects/lightweight-cryptography) and as the primary choice for lightweight authenticated encryption in the final portfolio of the [CAESAR competition (2014–2019)](https://competitions.cr.yp.to/caesar-submissions.html).

The Ascon family provides multiple different schemes; not all linked implementations implement all algorithms:

  * Authenticated encryption (`Ascon-128`, `Ascon-128a`, `Ascon-80pq`)
  
  * Hashing algorithms including hash functions with fixed 256-bit tag size (`Ascon-Hash`, `Ascon-Hasha`) and eXtendable Output Functions (XOFs) with variable output lengths (`Ascon-Xof`, `Ascon-Xofa`)

  * Authentication algorithms including Message Authentication Codes (MACs) with fixed 128-bit tag size (`Ascon-Mac`, `Ascon-Maca`)
  and PseudoRandom Functions (PRFs) with variable output lengths (`Ascon-Prf`, `Ascon-Prfa`), as well as a variant for short messages of up to 128 bits (`Ascon-PrfShort`)

Find the specification of Ascon v1.2 as submitted to NIST LWC and more information here: https://ascon.iaik.tugraz.at/


Software Implementations
------------------------

### C/C++

| Description | Code | Author | Comments and supported variants |
|-------------|------|--------|---------------------------------|
| :star: **C reference implementation** | https://github.com/ascon/ascon-c | Ascon Team | Features both the reference implementation and optimized implementations (64-bit) of Ascon-128 and Ascon-128a. For a detailed overview of the performance of Ascon-128 and Ascon-128a on different CPUs see [eBAEAD](https://bench.cr.yp.to/ebaead.html). |
| **C** collection with benchmarks | https://lab.las3.de/gitlab/lwc/candidates/tree/master/ascon/Implementations | Rhys Weatherley et al. | Collection with implementations by multiple authors, including benchmarking results (AEAD and hash variants) |
| **C** with Init-Update-Final interface | https://github.com/TheMatjaz/LibAscon | Matjaž Guštin | C11 library wrapping the reference C implementation (all AEAD and hash variants), including Init-Update-Final processing and variable tag length |
| **C/assembly** optimized for 32-bit architectures (ESP32/Xtensa, RISC-V) | [in LAS3 collection](https://lab.las3.de/gitlab/lwc/candidates/commit/9c6d9e4a880476fa74f439263cc2f4fc6f78940a) | Ferdinand Bachmann | C wrapper with assembly optimized for Tensilica Xtensa and 32-bit RISC-V (all AEAD and hash variants) |
| **C** optimized for RISC-V | https://github.com/ulmer-a/lightweight_aead | Alexander Ulmer | RISC-V implementation of Ascon-128 and Ascon-128a |


### Other Languages

| Description | Code | Author | Comments and supported variants |
|-------------|------|--------|---------------------------------|
| :star: **Python reference implementation** | https://github.com/meichlseder/pyascon | Ascon Team | Reference implementation of all AEAD and hash family members. Note: The [pypi package](https://pypi.org/project/ascon/) is not maintained by us. |
| **Cython/Python** | https://github.com/xHappenZ/cyascon | Oliver Popa | Python wrapper with C/Cython implementation (all AEAD and hash variants), with optional init-update-final interface.
| **Java** | https://github.com/ascon/javaascon | Hannes Groß | Java implementation of Ascon-128 and Ascon-128a. |
| **Java for JCE** | - | SIC | IAIK-LW Provider for the Java Cryptography Extension (JCE). Links: [commercial toolkit](https://jce.iaik.tugraz.at/products/core-crypto-toolkits/ascon-lightweight-crypto-toolkit/), [free evaluation version](https://jce.iaik.tugraz.at/product/iaik-lightweight-provider-evaluation-version/) |
| **Rust** | https://github.com/RustCrypto/hashes/tree/master/ascon-hash, https://github.com/RustCrypto/AEADs/tree/master/ascon-aead | Sebastian Ramacher | Rust implementation, as part of the RustCrypto library, of all AEAD and hash variants. Links: [git (hash)](https://github.com/RustCrypto/hashes/tree/master/ascon-hash), [git (AEAD)](https://github.com/RustCrypto/AEADs/tree/master/ascon-aead), [crate (hash)](https://crates.io/crates/ascon-hash), [crate (AEAD)](https://crates.io/crates/ascon-aead) |
| **Jasmin** | https://github.com/jerlacher/ascon-jasmin | Johannes Erlacher | Jasmin implementation with a Rust interface (Ascon-128 and Ascon-128a AEAD variants) |
| **Go** | https://ascon.iaik.tugraz.at/www.github.com/cloudflare/circl | Armando Faz | Go implementation as part of the CIRCL library (all AEAD variants) |
| **TypeScript** | https://github.com/Simolation/ascon-js | Simon Osterlehner | Fully typed TypeScript/JavaScript library (all AEAD and hash variants). Link: [npm](https://www.npmjs.com/package/ascon-js) |
| **TypeScript/JavaScript** | https://github.com/brainfoolong/js-ascon | Roland Eigelsreiter | JavaScript/TypeScript implementation (all Ascon family members). Link: [npm](https://www.npmjs.com/package/js-ascon) |
| **PHP** | https://github.com/brainfoolong/php-ascon | Roland Eigelsreiter | PHP 8+ implementation (all Ascon family members) |
| **Zig** | https://github.com/ziglang/zig/blob/master/lib/std/crypto/ascon.zig | Frank Denis | Zig implementation as part of the standard library (permutation only) |


Hardware Implementations
------------------------

:construction: to be completed


Co-Processor
------------

:construction: to be completed


Benchmarks
----------

:construction: to be completed


