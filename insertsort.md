**Problem:**

>Create insertion sort program in Rustprogramming Language

> input: is a Vector [12,34,32,11,56,2]
> output: print the arrary elements in sorted format

>If you are not sure how sorting algorithm works :
  Clue: One loop read the elements of the from left right from second element onwards.
        from the first loop point element will be picked and checked from right to left most in the second and insert
        correct position.
        
 | 12 | 34 | 32 | 11 | 56 | 2 |
 |----|----|----|----|----|----|
 | 12 | **34** | 32 | 11 | 56 | 2 | 
 | 12 | 32 | **34** | 11 | 56 | 2 |
 | 11 | 12 | 32 | **34** | 56 | 2 |
 | 11 | 12 | 32 | 34 | **56** | 2 |
 | 2 | 11 | 12 | 32 | 34 | **56** | 
 

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
