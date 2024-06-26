```rust
static CONTENT: &'static str =
    "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam,
quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo
consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse
cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non
proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
";

use std::fs::File;
use std::io::prelude::*;
use std::path::Path;

fn main() {
    let path = Path::new("lorem_ipsum.txt");
    let display = path.display();

    let mut file = match File::create(&path) {
        Err(why) => panic!("couldn't create {}: {}", display, (&why.to_string())),
        Ok(file) => file,
    };

    // variant which does not exit:
    // let mut file = match File::create(&path) {
    //     Err(why) => { println!("couldn't create {}: {}",
    //                        display,
    //                        Error::description(&why));
    //                   return
    //               },
    //     Ok(file) => file,
    // };

    match file.write_all(CONTENT.as_bytes()) {
        Err(why) => {
            panic!(
                "couldn't write to {}: {}",
                display,
                (&why.to_string())
            )
        }
        Ok(_) => println!("successfully wrote to {}", display),
    }

    // variant with if-test on successfull write:
    if file.write(CONTENT.as_bytes()).is_err() {
        // error-text not available anymore
        println!("Failed to save response.");
        return;
    }
}
// successfully wrote to lorem_ipsum.txt

```
[Run in Rust Playground](https://play.rust-lang.org/?version=stable&mode=debug&edition=2021&gist=4ec9479f5a16e49c07c04120a4dffc32&version=stable)
