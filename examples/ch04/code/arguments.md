```rust
use std::env;

fn main() {
    // command-line arguments:
    let args: Vec<String> = env::args().collect();
    println!("The program's name is: {}", args[0]);
    for arg in args.iter() {
        println!("Next argument is: {}", arg)
    }
    println!("");
    println!("I got: {} arfguments", args.len() - 1);
    for n in 1..args.len() {
        println!("The {}th argument is {}", n, args[n]);
    }
    // slice pattern is experimental (see issue #23121)
    // match &args[..] {
    //  [ref progname] => { no() }, // no arguments passed
    //  [_, ref arg1] => { one() }, // one argument passed
    //  [_, ref arg1, ref arg2] => { two() }, // two arguments passed
    //  _ => { help(); } // all the other cases
    // }

    // OS-environment variables:
    println!("");
    let osvars = env::vars();
    for (key, value) in osvars {
        println!("{}: {}", key, value);
    }
}

// fn no() { println!("no arguments");}
// fn one() { println!("one argument");}
// fn two() { println!("two arguments"); }

// fn help() {
//     println!("Usage:
//               arguments <string> Check whether string is ok.
//               arguments func1 <integer> Apply func1 to integer");
// }

```
[Run in Rust Playground](https://play.rust-lang.org/?version=stable&mode=debug&edition=2021&gist=9ca37bd07a48338cca0b4ba795a9ad91&version=stable)
