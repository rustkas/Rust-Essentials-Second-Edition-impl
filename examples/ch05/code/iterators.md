```rust
#[allow(unused_variables)]
fn main() {
    // iterating over a range:
    let mut rng = 0..7;

    println!("> {:?}", rng.next()); // Some(0)
    println!("> {:?}", rng.next()); // Some(1)

    for n in rng {
        print!("{} - ", n);
    } // 2 - 3 - 4 - 5 - 6 -
    println!("");

    // iterating over arrays and vectors:
    let aliens = ["Cherfer", "Fynock", "Shirack", "Zuxu"];
    println!("Here are the aliens: ");
    for alien in aliens.iter() {
        print!("{} / ", alien)
    }
    println!("");
    
    // shorter way:
    println!("Here are the aliens again: ");
    for alien in &aliens {
        print!("{} / ", alien)
    }
    println!("");

    println!("Here are the aliens in reverse: ");
    for alien in aliens.iter().rev() {
        print!("{} / ", alien)
    }

    // lazy iterator:
    let rng = 0..1000_000;
}
// > Some(0)
// > Some(1)
// 23456
// 2 - 3 - 4 - 5 - 6 -
// Here are the aliens:
// Cherfer / Fynock / Shirack / Zuxu /
// Here are the aliens again:
// Cherfer / Fynock / Shirack / Zuxu /
// Here are the aliens in reverse:
// Zuxu / Shirack / Fynock / Cherfer /

```
[Run in Rust Playground](https://play.rust-lang.org/?version=stable&mode=debug&edition=2021&gist=477a9c60b3e9bd86ee6b95e12cf6d5d7&version=stable)
