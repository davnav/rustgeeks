**Problem:(Easy)**

> create a Merge function for 2 vectors merge together to single vector using Rust programming language

> input: Vector1 [2,3,4,5] and Vector 2 = [6,7,19,20]
> output: print the Vector as [2,3,4,5,6,7,19,20

Note : Vector and Arrays are different in Rust on how/where data stores

>hint: You can use 'push' method to add element into a Vector 


 
 

**Solution1**

```
  //main program which call the merge function
  fn main(){
        // vector1   as mutable
        let mut v1 = vec![12,32,34,54];
        //vector2
        let v2 = vec![23,24,25,56];
        
        //calling merge function with first parameter as mutable reference to the 
         merge(&mut v1,  &v2 );

        println!("{:?}",v1);

}

//merge function accepts first parameter as a mutable reference to vector1 and immutable reference to Vector2
fn merge(v1:&mut Vec<i32>,v2: &Vec<i32>){

        //looping through vector 2 and getting the values . use ' * ' to get value from element reference 'e'
        for e in v2.iter(){
                v1.push(*e);
        }

}

     
```
