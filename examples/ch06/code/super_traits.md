```rust
#[allow(dead_code)]
struct Zombie {
    health: u32,
    damage: u32,
}

trait SuperMonster {
    fn super1(&self);
}

trait Monster: SuperMonster {
    fn new(hlt: u32, dam: u32) -> Self;
    fn attack(&self);
    fn noise(&self) -> &'static str;
}

impl SuperMonster for Zombie {
    fn super1(&self) {
        println!("I am a SuperMonster");
    }
}

impl Monster for Zombie {
    fn new(mut h: u32, d: u32) -> Zombie {
        if h > 100 {
            h = 100;
        }
        Zombie {
            health: h,
            damage: d,
        }
    }

    fn attack(&self) {
        println!(
            "The Zombie bites! Your health lowers with {} damage points.",
            2 * self.damage
        );
    }

    fn noise(&self) -> &'static str {
        "Aaargh!"
    }
}

#[allow(unused_variables)]
fn main() {
    let zmb1 = Zombie {
        health: 75,
        damage: 15,
    };
    let zmb1 = Zombie::new(75, 15);
    
    zmb1.attack();
    println!("Oh no, I hear: {}", zmb1.noise());
    zmb1.super1();
}
// Oh no, I hear: Aaargh!
// I am a SuperMonster



```
[Run in Rust Playground](https://play.rust-lang.org/?version=stable&mode=debug&edition=2021&gist=e662dca2a05ed19f1c6c1b5a41be145e&version=stable)
