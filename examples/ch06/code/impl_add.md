```rust
use std::ops::Add;

#[derive(Debug)]
struct AType {
    value: i32,
}

impl AType {
    fn new(value: i32) -> AType {
        AType { value: value }
    }
}

impl Add for AType {
    type Output = AType;

    fn add(self, other: AType) -> AType {
        AType {
            value: self.value + other.value,
        }
    }
}
#[allow(dead_code)]
fn main() {
    let at1 = AType { value: 7 };
    let at2 = AType { value: 42 };
    let at3 = at1.add(at2);
    println!("{:?}", at3);

    {
        let at4 = AType { value: 2 };
        let at5 = AType { value: 108 };
        let at6 = at4 + at5;
        println!("{:?}", at6);
    }

    {
        let at4 = AType::new(2);
        let at5 = AType::new(108);
        let at6 = at4 + at5;
        println!("{:?}", at6);
    }
}
// AType { value: 49 }
// AType { value: 110 }

```
[Run in Rust Playground](https://play.rust-lang.org/?version=stable&mode=debug&edition=2021&gist=8f99e11b8e5bdb940772c106cab63dd6&version=stable)
