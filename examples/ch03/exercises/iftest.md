```rust
#[allow(unused_variables)]
fn main() {
    // 1) ; after expressions:
    let adult = true;
    let age = if adult {
        "+18";
    } else {
        "-18";
    };
    println!("Age is {:?}", age); // Age is ()
                                  // the following gives
                                  // error [E0308]: mismatched types: expected (), found &str
                                  // let age: &str = if adult { "+18"; } else { "-18"; };

    // 2) block without {  } ?
    // let n = 10;
    // if n > 5  println!("n is bigger than 5");
    // error: expected `{`, found `println`
    // help: place this code inside a block

    // 3) block without {  } ?
    let health = -3;
    let result = if health <= 0 {
        "Game over man!"
    } else {
        "Go on"
    };
    // error: if may be missing an else clause:
    // expected (), found &str
    // This doesn't work because the absence of the else part is viewed as else { () }
    // where () is a unit value of type (), which is not of type string
    // correction:
    let result = if health <= 0 { "Game over man!" } else { "" };
}
```
[Run in Rust Playground](https://play.rust-lang.org/?version=stable&mode=debug&edition=2021&gist=0bd61bec2958bed36a41ae0a7934c99c&version=stable)
