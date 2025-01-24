# Fixing "linking with `cc` failed: exit status: 1" Error

This error commonly occurs on MacOS systems, particularly on M1 machines, but can also appear on earlier versions of MacOS.

## Solution

The issue can be resolved by configuring Rust's linker settings. Create or modify the `~/.cargo/config.toml` file with the following content:

```toml
[target.x86_64-apple-darwin]
rustflags = [
  "-C", "link-arg=-undefined",
  "-C", "link-arg=dynamic_lookup",
]

[target.aarch64-apple-darwin]
rustflags = [
  "-C", "link-arg=-undefined",
  "-C", "link-arg=dynamic_lookup",
]
```

This configuration sets up the necessary linker arguments for both Intel (x86_64) and Apple Silicon (aarch64) architectures.

## Additional Information

- The configuration file path follows the [Cargo configuration format](https://doc.rust-lang.org/cargo/reference/config.html)
- This solution is based on community recommendations from [Stack Overflow](https://stackoverflow.com/questions/28124221/error-linking-with-cc-failed-exit-code-1)
