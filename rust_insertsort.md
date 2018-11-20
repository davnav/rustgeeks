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
 
 Insert Sort(https://en.wikipedia.org/wiki/Insertion_sort)
 
 

**Solution1**

```
  //function for insert sort logic
  
  fn insertsort(v:&Vec<i32>) -> i32 {
  
  //first "for" loop to get elements from second position to last element ( left to right )
  
    for i in 1..v.len(){
      let key = v[i];
      let mut j = i-1;
      
   //the last iteration needs to handle seperately, because j is taken an unsigned integer. so that last case loop execute
   //if we give condition j>=0, but we have j = j-1 statement which will get panic when it goes negative.
   
   //second while loop to iterate reverse direction( right to left ) from the first loop element which we call it as "key"
   
      while j>0 && v[j] > key{
              v[j+1] = v[j];
              j = j-1;
      }

     v[j+1] = key;
     
   // last iteration step handled seperately with if condition.
    if j==0 && v[0] > key{
          v[1] = v[0];
          v[0] = key;
    }else{
          v[j+1] = key;
    }


  }
    
  //main program which call the function
  fn main() {
 
      //declare the vector Read more on Vector here [https://github.com/nrc/r4cppp/blob/master/arrays.md]
      let mut v = vec![12,34,32,11,56,2];
      
      //call the function with mutable reference as we need to change the Vector elements position
      insertsort(&mut v);
      
      //print the vector elements
      println!("{:?}",v);
      
  }
```
