# ff

`ff` is a finite field library written in pure Rust, with no `unsafe{}` code.

## Disclaimers

* This library does not provide constant-time guarantees.
* This library relies on Rust's `i128_type` feature, which is currently only  available in the nightly compiler.

## Usage

Add the `ff` crate to your `Cargo.toml`:

```toml
[dependencies]
ff = "0.1"
```

The `ff` crate contains `Field`, `PrimeField`, `PrimeFieldRepr` and `SqrtField` traits. See the **[documentation](http)** for more.

### #![derive(PrimeField)]

If you need an implementation of a prime field, this library also provides a procedural macro that will expand into an efficient implementation of a prime field when supplied with the modulus. `PrimeFieldGenerator` must be an element of Fp of p-1 order, that is also quadratic nonresidue.

```rust
extern crate rand;
#[macro_use]
extern crate ff;

#[derive(PrimeField)]
#[PrimeFieldModulus = "52435875175126190479447740508185965837690552500527637822603658699938581184513"]
#[PrimeFieldGenerator = "7"]
struct Fp(FpRepr);
```

And that's it! `Fp` now implements `Field` and `PrimeField`. `Fp` will also implement `SqrtField` if supported. The library implements `FpRepr` itself and derives `PrimeFieldRepr` for it.

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
