**Problem:**

>Create a program to find a largest String from from the two Strings given

>String is handled differently in Rust programming language. Strings need to be handled carefully, otherwise it cause segmenation 
fault in C like programming languages.So it is necessary to read [https://doc.rust-lang.org/book/second-edition/ch08-02-strings.html]
(https://doc.rust-lang.org/book/second-edition/ch08-02-strings.html)

**Solution**

```
  //function for addtion which accepts 2 integer parameters and return an integer
  
  fn add(x: i32, y: i32) -> i32 {
    //calculate the sum and the expression get evaluated and return back, note there is no ";" for the statement 
    x + y
  }
  //main program which call the function
  fn main() {
      let m = add(1,2);
      println!("{}", m);
  }
```

As all programming language we need to create a main function in Rust. In main function we are calling the function "add" 
hardcoded values 1 and 2. Since the Rust is dynamically typed language, the values types will be considered as integers. 
The function definition should start with keyword **fn**. The add functions receiving parameters are 'x' and 'y' variables.
Here you might have noticed the we need to explicitly provide the types of the parameters. The return value type also need 
to given with **->** symbol.
