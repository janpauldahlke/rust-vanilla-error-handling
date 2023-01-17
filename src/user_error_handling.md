# Error handling by the user

Errors need to be displayed as strings!

That is why all errors implement the [`std::error::Error`](https://doc.rust-lang.org/std/error/trait.Error.html)
trait which requires that the `Debug` and the `Display` traits are implemented.

```rust
use std::fmt;

#[derive(Debug)]
pub struct MyError {
  message: String
}


//background is that the error Trait needs the Debug and the Display Trait
//impl traits has two ways, so 
//via derive macro
//of via impls ftm::Display which we need to use std::ftm;

//jörn advices us to copy paste it

//copy paste it, 

impl fmt::Display for MyError {
  // I copy & paste this code snippet every time
  fn fmt(&self, f: &mut fmt::Formatter<'_>) -> fmt::Result {
          write!(f, "{}", self.message)  // note the lack of semicolon
      }
}

impl std::error::Error for MyError {} // look, no code!

```
