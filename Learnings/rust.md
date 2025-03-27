## Modules

*Using **use** to create a public scope*
For example using a crate io
`use ::std::io`
- use `pub` keyword to make modules public
- By default everything is private in a module
- Rust has `as` keyword similar to python which enables renaming a module

## Common Collections
### Vectors
- Creation: `let v:Vec<i32> = Vec::new();` or `let v:Vec<i32> = Vec![1,2,3]`
- Iteration: `for element in my_vec {}` or `for element in &v`
- Borrowing: `&v` for constant reference and `&mut v` for a mutable one
- Inserting: `v.push(element);`
### Strings
- String types are many `String, &str, OsString` etc. Only two types are primary `String` and `&str`. `String` exits on heap whereas &str is stored in the binary.
- Creation: `let mut s = String::new()` or `let mut s = String::from("someStringLiteral")`
- Updating Contents: `s.push_str("bar")` to add a String literal or a String type. `s.push("c")` => adds a single character to the string and only take a single character.
### Hash Maps
- Import: `use std::collections::HashMap`
- Creation: `let myMap = HashMap::new()`
- Adding: `mymap.insert()`
- Adding if key exists or not `mymap.entry("String").or_insert(default:value)`