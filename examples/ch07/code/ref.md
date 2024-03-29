```rust
#[allow(dead_code)]
struct Magician {
	name: &'static str,
	power: u32
}

fn main() {
	let n = 42;
	match n {
    	ref r => println!("Got a reference to {}", r),
	}

	let mut m = 42;
	match m {
    	ref mut mr => {
    		println!("Got a mutable reference to {}", mr);
    		*mr = 43;
    	},
	}
	println!("m has changed to {}!", m);

	let mag = Magician { name: "Gandalf", power: 4625 };
	let name = {
        // `ref_to_x` is a reference to the `x` field
        let Magician { name: ref ref_to_name, power: _ } = mag;
        // Return a copy of the `name` field of `mag`
        *ref_to_name
    };
    println!("The magician's name is {}", name);
}
// Got a reference to 42
// Got a mutable reference to 42
// m has changed to 43!
// The magician's name is Gandalf
```
[Run in Rust Playground](https://play.rust-lang.org/?version=stable&mode=debug&edition=2021&gist=98a06b4db9fd1f18bd927a5239ac0643&version=stable)
