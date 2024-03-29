```rust
struct Player {
    nname: &'static str, // nickname
    health: i32,
    level: u8,
}

#[allow(dead_code)]
fn main() {

    struct Scoreu; // unit struct

    // tuple structs:
    struct Score(i32, u8);
    let score1 = Score(73, 2); // make (instantiate) a tuple struct
    let Score(h, l) = score1; // // extract values by destructuring
    println!("Health {} - Level {}", h, l);

    // newtype:
    struct Kilograms(u32);
    let weight = Kilograms(250);
    let Kilograms(kgm) = weight; // extracting kgm
    println!("weight is {} kilograms", kgm);

    // struct:
    let mut pl1 = Player {
        nname: "Dzenan",
        health: 73,
        level: 2,
    };
    println!("Player 1 {} is at level {}", pl1.nname, pl1.level);
    pl1.level = 3;

    // update syntax:
    let pl2 = Player {
        nname: "Ivo",
        ..pl1
    };
    println!("Player 2 {} is at level {}", pl2.nname, pl2.level);

    // destructuring a struct:
    let Player {
        health: ht,
        nname: nn,
        ..
    } = pl1;
    println!("Player {} has health {}", nn, ht);

    // pointers do automatic dereferencing when accessing data structure elements:
    let ps = &Player {
        nname: "John",
        health: 95,
        level: 1,
    };
    println!("{} == {}", ps.nname, (*ps).nname);
}
// Health 73 - Level 2
// weight is 250 kilograms
// Player 1 Dzenan is at level 2
// Player 2 Ivo is at level 3
// Player Dzenan has health 73
// John == John

```
[Run in Rust Playground](https://play.rust-lang.org/?version=stable&mode=debug&edition=2021&gist=5d018c59ddad214264ab3b120f67a9c3&version=stable)
