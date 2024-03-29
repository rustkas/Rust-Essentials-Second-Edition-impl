```rust
struct Alien {
    health: u32,
    damage: u32,
}

impl Alien {
    fn new(mut h: u32, d: u32) -> Alien {
        // constraints:
        if h > 100 {
            h = 100;
        }
        Alien {
            health: h,
            damage: d,
        }
    }

    fn warn() -> &'static str {
        "Leave this planet immediately or perish!"
    }

    fn attack(&mut self) {
        println!(
            "I attack! Your health lowers with {} damage points.",
            self.damage
        );
        self.health -= self.damage;
    }

    // multiple errors:
    // cannot assign to immutable field self.health
    //     solution: &mut self
    // duplicate definition of value `attack`
    //	   solution: give method a different name
    // fn attack(&mut self) {
    // 	self.health -= 10;
    // }

    fn attack_and_suffer(&mut self, damage_from_other: u32) {
        println!(
            "I attack! Your health lowers with {} damage points.",
            self.damage
        );
        self.health -= damage_from_other;
    }
}

#[allow(unused_variables, unused_mut)]
fn main() {
    let mut bork = Alien {
        health: 100,
        damage: 5,
    };
    let mut berserk = Alien::new(150, 15);
    println!("The berserk's health at birth is: {}", berserk.health);
    println!("{}", Alien::warn());
    berserk.attack();
    println!("The berserk's health is: {}", berserk.health);
    berserk.attack_and_suffer(31);
    println!("After attack the berserk's health is: {}", berserk.health);
}
// The berserk's health at birth is: 100
// Leave this planet immediately or perish!
// I attack! Your health lowers with 15 damage points.
// The berserk's health is: 100
// After attack the berserk's health is: 69

```
[Run in Rust Playground](https://play.rust-lang.org/?version=stable&mode=debug&edition=2021&gist=954569b8f6f48e84d6b57178fe5bdd62&version=stable)
