<div align="center">

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/d/d5/Rust_programming_language_black_logo.svg/1024px-Rust_programming_language_black_logo.svg.png" width="90" height="90" alt="Rust logo" />

<h1>Algorithms and Data Structures in Rust</h1>

<p>Educational, idiomatic Rust implementations of classic algorithms and data structures.</p>

</div>

## Overview

This crate collects implementations across many domains, written in safe Rust 2021 and organized by topic. It can be used both as a learning resource and as a library you can call from your own projects.

Highlights:
- Broad coverage: backtracking, big integers, bit manipulation, ciphers/crypto primitives, compression, conversions, data structures, dynamic programming, graphs, greedy, math, number theory, searching, sorting, strings, and more.
- Pure Rust with optional big integer support.
- Property-based tests using QuickCheck.

## Getting started

Prerequisites:
- Rust toolchain installed via rustup (stable).

Build and test:
- Build: `cargo build`
- Run tests: `cargo test`
- Lint: `cargo clippy --all-targets --all-features`
- Format: `cargo fmt`

### Features

This crate exposes an optional feature for big integer math:
- `big-math` (default): enables `num-bigint` and `num-traits`.

Examples:
- Disable default features: `cargo test --no-default-features`
- Enable explicitly: `cargo build --features big-math`

## Use as a library

Add this crate to another project. If you are developing locally, use a path dependency in your project's `Cargo.toml`:

```toml
[dependencies]
the_algorithms_rust = { path = "../Rust" }
```

Example usage:

```rust
use the_algorithms_rust::sorting::{is_sorted, quick_sort};

fn main() {
    let mut v = vec![6, 5, 4, 3, 2, 1];
    quick_sort(&mut v);
    assert!(is_sorted(&v));
}
```

## Project structure

Each top-level module in `src/` groups related algorithms:

- `backtracking/`: N-Queens, Hamiltonian cycle, graph coloring, Sudoku, permutations, combinations, etc.
- `big_integer/`: big integer utilities and examples (e.g., fast factorial, multiply, Poly1305).
- `bit_manipulation/`: counting bits, Gray code, highest set bit, sum without `+`.
- `ciphers/`: classical ciphers and hashing primitives (AES, BLAKE2b, ChaCha/Salsa, SHA-2/3, Vigenère, ROT13, Diffie–Hellman, etc.). See `ciphers/README.md` for details.
- `compression/`: run-length encoding, move-to-front.
- `conversions/`: base conversions and color/length conversions.
- `data_structures/`: AVL/B-trees, BST, Fenwick tree, heaps, segment trees, union-find, tries, hash tables, graphs, linked lists, queues, stacks, etc.
- `dynamic_programming/`: Fibonacci, LCS, knapsack, coin change, egg dropping, and more.
- `graph/`, `greedy/`, `math/`, `number_theory/`, `searching/`, `sorting/`, `string/`, ...: additional categories and algorithms.

Browse the source directories for per-algorithm implementations and unit tests.

## Testing and quality

- Unit tests live alongside implementations. Run all tests with `cargo test`.
- Property tests use `quickcheck`/`quickcheck_macros`.
- Clippy lints are configured in `Cargo.toml` and `clippy.toml`. Run `cargo clippy` before submitting changes.

## Contributing

Contributions are welcome. Suggested workflow:
- Add a new algorithm in the appropriate module folder with clear docs and tests.
- Keep APIs small and idiomatic; prefer safe Rust.
- Ensure `cargo build`, `cargo test`, `cargo fmt`, and `cargo clippy` pass.

## License

MIT License. See `LICENSE` for details. Portions of this work are based on or inspired by community implementations of algorithms in Rust.

