```rust
extern crate num;

fn sqroot<T: num::traits::Float>(r: T) -> Result<T, String> {
    if r < num::zero() {
        return Err("Number cannot be negative!".to_string());
    }
    Ok(num::traits::Float::sqrt(r))
}

// trait constraint written with where clause syntax:
fn sqroot2<T>(r: T) -> Result<T, String>
where
    T: num::traits::Float,
{
    if r < num::zero() {
        return Err("Number cannot be negative!".to_string());
    }
    Ok(num::traits::Float::sqrt(r))
}


// errors: binary operation `<` cannot be applied to type `T`
// no function or associated item named `sqrt` found for type `T` in
// the current scope
// fn sqroot3<T>(r: T) -> Result<T, String> {
//     if r < 0.0 {
//         return Err("Number cannot be negative!".to_string());
//     }
//     Ok(T::sqrt(r))
// }

fn main() {
    println!("The square root of {} is {:?}", 42.0f32, sqroot(42.0f32));
    println!("The square root of {} is {:?}", 42.0f64, sqroot2(42.0f64));
    // println!("The square root of {} is {:?}", 42, sqroot(42));
}



// The square root of 42 is Ok(6.4807405)
// The square root of 42 is Ok(6.48074069840786)

// fn multc<T: Trait1, U: Trait1 + Trait2>(x: T, y: U) {}
// fn multc<T, U>(x: T, y: U) where T: Trait1, U: Trait1 + Trait2 {}

```
[Run in Rust Playground](https://play.rust-lang.org/?version=stable&mode=debug&edition=2021&gist=8ee3998c06b3f0fa9a81c718792f79e5&version=stable)
