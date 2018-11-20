**Problem:(Medium)**

>Create insertion sort program in Rustprogramming Language

> input: is a Vector [12,34,32,11,56,2]
> output: print the Vector elements in sorted format

Note : Vector and Arrays are different in Rust on how/where data stores

>If you are not sure how insert sorting algorithm works :
  Clue: 1. One loop read the elements of the Vector from left to right from second element onwards to last element.
        2. from the first loop point element ( we can call it as Key) , we will compare from right to left and insert the key in the correct position
            
 | 12 | 34 | 32 | 11 | 56 | 2 |
 |----|----|----|----|----|----|
 | 12 | **34** | 32 | 11 | 56 | 2 | 
 | 12 | 32 | **34** | 11 | 56 | 2 |
 | 11 | 12 | 32 | **34** | 56 | 2 |
 | 11 | 12 | 32 | 34 | **56** | 2 |
 | 2 | 11 | 12 | 32 | 34 | **56** | 
 
 If you look at each iteration of the both loops above table of output will be getting generated , loops needs iteration only through bolded elements in diagonal of the square : (N * N)/2 
 
 ie time complexicity is O(n) = n^2
 
 [https://en.wikipedia.org/wiki/Insertion_sort]
 
 

**Solution**

```
  //function for insert logic
  
  fn insertsort(x: i32, y: i32) -> i32 {
    //calculate the sum and the expression get evaluated and return back, note there is no ";" for the statement 
    x + y
  }
  //main program which call the function
  fn main() {
      //declare the vector 
      let v = 
      println!("{}", m);
  }
```

As all programming language we need to create a main function in Rust. In main function we are calling the function "add" 
hardcoded values 1 and 2. Since the Rust is dynamically typed language, the values types will be considered as integers. 
The function definition should start with keyword **fn**. The add functions receiving parameters are 'x' and 'y' variables.
Here you might have noticed the we need to explicitly provide the types of the parameters. The return value type also need 
to given with **->** symbol.
