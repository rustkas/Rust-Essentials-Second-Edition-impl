```rust
use std::io;

fn main() {
    println!("What's your name, noble warrior?");
    let mut buf = String::new();
    // version with .ok().expect():
    io::stdin().read_line(&mut buf)
        .ok()
        .expect("Failed to read line");
    let name = buf.trim();
    println!("{}, that's a mighty name indeed!", name);

    //version with unwrap():
    io::stdin().read_line(&mut buf).unwrap();
    let name = buf.trim();
    println!("{}, that's a mighty name indeed!", name);

    // alternative with testing is_ok():
    if io::stdin().read_line(&mut buf).is_ok() {
        let name = buf.trim();
        println!("{}, that's a mighty name indeed!", name);
    } else {
        println!("Failed to read line!");
    }
}
// What's your name, noble warrior?
// Riddick
// Riddick, that's a mighty name indeed!

```
[Run in Rust Playground](https://play.rust-lang.org/?version=stable&mode=debug&edition=2021&gist=0c9707024672447ffd4f27764776fe87&version=stable)
