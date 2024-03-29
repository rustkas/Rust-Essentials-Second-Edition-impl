```rust
fn greet(name: &str) {
    println!("Hi mighty {name}, what brings you here?", name=name);
}

fn greet_both(name1: &str, name2: &str) {
    greet(name1);
    greet(name2);
}

fn increment_power(power: i32) -> i32 {
    // if power < 100 { return 999 }
    println!("My power is going to increase:");
    // power + 1; // results in: error[E0308]: mismatched types - not all control paths return a value
    // return power + 1 // poor style
    power + 1
}

fn double_input(mut i: u32) -> u32 {
    i = i * 2;
    i
}

// no need for a temporary mut variable:
fn double_inputs(i: u32) -> u32 {
    i * 2
}

fn main() {
    let hero1 = "Pac Man"; // is of type &str
    let hero2 = "Riddick";
    greet(hero2);
    greet_both(hero1, hero2);

    let power = increment_power(1);
    println!("I am now at power level: {}", power);
    assert_eq!(2, power);

    println!("{}", double_input(4));
    println!("{}", double_inputs(4));
}
// Hi mighty Riddick, what brings you here?
// Hi mighty Pac Man, what brings you here?
// Hi mighty Riddick, what brings you here?
// My power is going to increase:
// I am now at power level: 2
// 8
// 8

```
[Run in Rust Playground](https://play.rust-lang.org/?version=stable&mode=debug&edition=2021&gist=6be3aad763742a49d59507c3b95be404&version=stable)
