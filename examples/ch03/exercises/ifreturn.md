```rust
fn verbose(x: i32) -> &'static str {
    let result: &'static str;
    if x < 10 {
        result = "less than 10";
    } else {
        result = "10 or more";
    }
    return result;
}

fn simple(x: i32) -> &'static str {
    if x < 10 {
        "less than 10"
    } else {
        "10 or more"
    }
}

fn main() {
    let n = 13;
    println!("verbose: {}", verbose(n));
    println!("simple: {}", simple(n));
}
// verbose: 10 or more
// simple: 10 or more

```
[Run in Rust Playground](https://play.rust-lang.org/?version=stable&mode=debug&edition=2021&gist=bd0ea4742a512d21f1bb0405b22d0059&version=stable)
