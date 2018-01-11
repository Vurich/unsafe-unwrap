# `unsafe-unwrap`

Ever thought that `Option::unwrap` was convenient, but thought it wasn't quite
unsafe enough? Now you can cause undefined behaviour with ease! Simply put:

```rust
fn main() {
  use unsafe_unwrap::UnsafeUnwrap;

  unsafe { None::<()>.unwrap_unchecked() }
}
```

and see your program disappear before your very eyes:

```
error: process didn't exit successfully: `./unsafe-unwrap` (signal: 4, SIGILL: illegal instruction)
```

This means that now you don't have to deal with the draconian null-checking that
once plagued your Rust codebase and you can deref your nullable pointers the way
God intended: with utter confidence.

### Serious note

Your performance is almost certainly not important enough to use this crate. The
stdlib `unwrap` and `expect` methods are very fast - the check and the access
can usually happen in parallel since the branch is essentially perfectly
predictable and the failure path is marked as cold.
