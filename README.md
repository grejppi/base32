# base32 [![Build Status](https://travis-ci.org/andreasots/base32.svg?branch=master)](https://travis-ci.org/andreasots/base32)

This library lets you encode and decode in either [RFC4648 Base32](http://en.wikipedia.org/wiki/Base32#RFC_4648_Base32_alphabet), [Crockford Base32](http://en.wikipedia.org/wiki/Base32#Crockford.27s_Base32), or [z-base-32](https://en.wikipedia.org/wiki/Base32#z-base-32).

# Usage

```rust
use base32::Alphabet::{Crockford, RFC4648, ZBase32};

// crockford base32
assert_eq!(encode(Crockford, &[0xF8, 0x3E, 0x0F, 0x83, 0xE0]), "Z0Z0Z0Z0");
assert_eq!(decode(Crockford, "Z0Z0Z0Z0").unwrap(), [0xF8, 0x3E, 0x0F, 0x83, 0xE0]);

// rfc4648 base32
assert_eq!(encode(RFC4648 { padding: true }, &[0xF8, 0x3E, 0x7F, 0x83, 0xE7]), "7A7H7A7H");
assert_eq!(decode(RFC4648 { padding: true }, "7A7H7A7H").unwrap(), [0xF8, 0x3E, 0x7F, 0x83, 0xE7]);

// rfc4648 base32 without padding characters (=)
assert_eq!(encode(RFC4648 { padding: false }, &[0xF8, 0x3E, 0x7F, 0x83, 0xE7]), "7A7H7A7H");
assert_eq!(decode(RFC4648 { padding: false }, "7A7H7A7H").unwrap(), [0xF8, 0x3E, 0x7F, 0x83, 0xE7]);

// z-base-32
assert_eq!(encode(ZBase32, &[0xF8, 0x3E, 0x7F, 0x83, 0xE7]), "9y989y98");
assert_eq!(decode(ZBase32, "9y989y98").unwrap(), [0xF8, 0x3E, 0x7F, 0x83, 0xE7]);
```

## License

Licensed under either of

 * Apache License, Version 2.0, ([LICENSE-APACHE](LICENSE-APACHE) or http://www.apache.org/licenses/LICENSE-2.0)
 * MIT license ([LICENSE-MIT](LICENSE-MIT) or http://opensource.org/licenses/MIT)

at your option.

### Contribution

Unless you explicitly state otherwise, any contribution intentionally
submitted for inclusion in the work by you, as defined in the Apache-2.0
license, shall be dual licensed as above, without any additional terms or
conditions.
