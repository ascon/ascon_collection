Implementations of the Ascon Family
===================================

This is a collection of hardware and software implementations of Ascon.
Reference implementations are included as submodules, while this file lists additional implementations in various languages.

:warning: Some repositories implement the published standard [NIST SP 800-232](https://csrc.nist.gov/pubs/sp/800/232/final), while others implement the submitted candidate design, which are not compatible.
Linked implementations may become outdated or incorrect and should not be used for productive environments without caution.


About Ascon
-----------

[Ascon](https://ascon.isec.tugraz.at) is a family of [authenticated encryption](https://en.wikipedia.org/wiki/Authenticated_encryption) (AEAD) and [hashing](https://en.wikipedia.org/wiki/Cryptographic_hash_function) algorithms designed to be lightweight and easy to implement, even with added countermeasures against side-channel attacks.
It was designed by a team of cryptographers from Graz University of Technology, Infineon Technologies, and Intel Labs: Christoph Dobraunig, Maria Eichlseder, Florian Mendel, and Martin Schläffer.

Ascon has been selected as the standard for lightweight cryptography in the [NIST Lightweight Cryptography competition (2019–2023)](https://csrc.nist.gov/projects/lightweight-cryptography) and as the primary choice for lightweight authenticated encryption in the final portfolio of the [CAESAR competition (2014–2019)](https://competitions.cr.yp.to/caesar-submissions.html).

**The standardized and most recent version** of Ascon is specified in [NIST SP 800-232](https://csrc.nist.gov/pubs/sp/800/232/final) and includes the following designs:

  * Authenticated Encryption with Associated Data (AEAD):

    - `Ascon-AEAD128` with 128-bit key, nonce, and tag
  
  * Hashing algorithms:
  
    - `Ascon-Hash256` with fixed 256-bit output size (hash function)
    - `Ascon-XOF128` with variable output lengths (eXtendable Output Function, XOF)
    - `Ascon-CXOF128` with variable output lengths and supporting a customization string as an additional input (Customizable XOF)


**Prior versions** (Ascon v1.2 as submitted to NIST LWC) and other non-standardized family members include:

  * Authenticated encryption (`Ascon-128`, `Ascon-128a`, `Ascon-80pq`)
  
  * Hashing algorithms including hash functions with fixed 256-bit tag size (`Ascon-Hash`, `Ascon-Hasha`) and eXtendable Output Functions (XOFs) with variable output lengths (`Ascon-Xof`, `Ascon-Xofa`)

  * Authentication algorithms including Message Authentication Codes (MACs) with fixed 128-bit tag size (`Ascon-Mac`, `Ascon-Maca`)
  and PseudoRandom Functions (PRFs) with variable output lengths (`Ascon-Prf`, `Ascon-Prfa`), as well as a variant for short messages of up to 128 bits (`Ascon-PrfShort`)


Find the specification of Ascon and more information here: https://ascon.isec.tugraz.at/


Software Implementations
------------------------

### C/C++

| Description | Code | Author | Ascon version | Comments and supported variants |
|-------------|------|--------|---------------|---------------------------------|
| :star: **C reference implementation** | [ascon/ascon-c](https://github.com/ascon/ascon-c) | Ascon Team | NIST SP 800-232 | Features both the reference implementation and optimized implementations (64-bit) of all AEAD and hash family members. For a detailed overview of the AEAD performance on different CPUs see [eBAEAD](https://bench.cr.yp.to/ebaead.html). |
| **C** collection with benchmarks | [lab.las3.de/lwc/ascon](https://lab.las3.de/gitlab/lwc/candidates/tree/master/ascon/Implementations) | Rhys Weatherley et al. | LWC submission | Collection with implementations by multiple authors, including benchmarking results (AEAD and hash variants) |
| **C** with Init-Update-Final interface | [TheMatjaz/LibAscon](https://github.com/TheMatjaz/LibAscon) | Matjaž Guštin | LWC submission | C11 library wrapping the reference C implementation (all AEAD and hash variants), including Init-Update-Final processing and variable tag length |
| **C/assembly** optimized for 32-bit architectures (ESP32/Xtensa, RISC-V) | [in LAS3 collection](https://lab.las3.de/gitlab/lwc/candidates/commit/9c6d9e4a880476fa74f439263cc2f4fc6f78940a) | Ferdinand Bachmann | LWC submission | C wrapper with assembly optimized for Tensilica Xtensa and 32-bit RISC-V (all AEAD and hash variants) |
| **C** optimized for RISC-V | [ulmer-a/lightweight_aead](https://github.com/ulmer-a/lightweight_aead) | Alexander Ulmer | LWC submission | RISC-V implementation of Ascon-128 and Ascon-128a |
| **C** with Init-Update-Final interface | [platsec/sp800232-rit](https://gitlab.com/platsec/sp800232-rit) | Billy Brumley | NIST SP 800-232 | Cleanroom C implementation, including Init-Update-Final processing |


### Other Languages

| Description | Code | Author | Ascon version | Comments and supported variants |
|-------------|------|--------|---------------|---------------------------------|
| :star: **Python reference implementation** | [meichlseder/pyascon](https://github.com/meichlseder/pyascon) | Ascon Team | NIST SP 800-232  | Reference implementation of all AEAD and hash family members. Note: The [pypi package](https://pypi.org/project/ascon/) is not maintained by us. |
| **Rust** | [sebastinas/ascon-hash](https://github.com/sebastinas/ascon-aead/tree/main/ascon-hash), [sebastinas/ascon-aead](https://github.com/sebastinas/ascon-aead/tree/main/ascon-aead) | Sebastian Ramacher | NIST SP 800-232  | Rust implementation, implementing the RustCrypto traits, of all AEAD and hash variants. Crate links: [crate (hash)](https://crates.io/crates/ascon-hash), [crate (AEAD)](https://crates.io/crates/ascon-aead) |
| **TypeScript/JavaScript** | [brainfoolong/js-ascon](https://github.com/brainfoolong/js-ascon) | Roland Eigelsreiter | NIST SP 800-232  | JavaScript/TypeScript implementation (all Ascon family members). Link: [npm](https://www.npmjs.com/package/js-ascon) |
| **PHP** | [brainfoolong/php-ascon](https://github.com/brainfoolong/php-ascon) | Roland Eigelsreiter | NIST SP 800-232  | PHP 8+ implementation (all Ascon family members) |
| **Web interface (JavaScript)** | [motarekk.github.io](https://motarekk.github.io/) | Mohamed Tarek | NIST SP 800-232  | `playascon` is an interactive website that encrypts/hashes any user-provided data using a JavaScript implementation (all Ascon family members) |
| **Cython/Python** | [xHappenZ/cyascon](https://github.com/xHappenZ/cyascon) | Oliver Popa | LWC submission | Python wrapper with C/Cython implementation (all AEAD and hash variants), with optional init-update-final interface. |
| **Java for JCE** | - | SIC | LWC submission | IAIK-LW Provider for the Java Cryptography Extension (JCE). Links: [commercial toolkit](https://jce.isec.tugraz.at/products/core-crypto-toolkits/ascon-lightweight-crypto-toolkit/), [free evaluation version](https://jce.isec.tugraz.at/product/iaik-lightweight-provider-evaluation-version/) |
| **Jasmin** | [jerlacher/ascon-jasmin](https://github.com/jerlacher/ascon-jasmin) | Johannes Erlacher | LWC submission | Jasmin implementation with a Rust interface (Ascon-128 and Ascon-128a AEAD variants) |
| **Go** | [cloudflare/circl](https://github.com/cloudflare/circl) | Armando Faz | LWC submission | Go implementation as part of the CIRCL library (all AEAD variants) |
| **TypeScript** | [Simolation/ascon-js](https://github.com/Simolation/ascon-js) | Simon Osterlehner | LWC submission | Fully typed TypeScript/JavaScript library (all AEAD and hash variants). Link: [npm](https://www.npmjs.com/package/ascon-js) |
| **Zig** | [ziglang/ascon.zig](https://github.com/ziglang/zig/blob/master/lib/std/crypto/ascon.zig) | Frank Denis | LWC submission | Zig implementation as part of the standard library (permutation only) |
| **Java** | [ascon/javaascon](https://github.com/ascon/javaascon) | Hannes Groß | CAESAR submission | Java implementation of Ascon-128 and Ascon-128a. |


Hardware Implementations
------------------------

:construction: to be completed


Protected Implementations
-------------------------

| Description | Code | Author | Ascon version | Comments and supported variants |
|-------------|------|--------|---------------|---------------------------------|
| **RISC-V** (RV32IM assembly) | [l.mainka/side-channel-secure-ascon](https://uva-hva.gitlab.host/l.mainka/side-channel-secure-ascon) | Linus Mainka, Kostas Papagiannopoulos | LWC submission | Protected RISC-V implementation of Ascon-128 using masking and shuffling ([CASCADE 2025 paper preprint](https://eprint.iacr.org/2025/564)). |

:construction: to be completed


Co-Processor
------------

:construction: to be completed


Benchmarks
----------

:construction: to be completed


