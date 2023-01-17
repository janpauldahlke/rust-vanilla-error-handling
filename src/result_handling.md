# Error handling with Result

* consider this a recoverable error, check on how the Err can be still handled with code in the Result:Error

We can handle errors by looking at the state of the `Result`:

```rust
let cake = loop {
  match bake_cake() {
    Result::Ok(the_cake) => break the_cake,
    Result::Err(some_error) => {
      eprintln!("{}", &some_error.description);
      clean_up_the_mess(&some_error.step);
      buy_new_ingredients(&some_error.step);
    }
  } // run forever until we have a cake
}
```
