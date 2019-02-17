**Problem:(Medium)**

> Find the nth element in Fibonaaci series using Dynamic programming in Rust

>hint: You can use HashMap to store elements<br>
> fib(n) = fib(n-1) + fib(n-2)


 
 

**Solution1**

```
 
 //Fibonacci with Dynamic programming using Hashmap

use std::collections::HashMap;


fn fib(n:u8,memo:&mut HashMap<u8,u8>) -> u8{

        if n <= 2{


                *memo.get_mut(&1).unwrap() = 0;
                *memo.get_mut(&2).unwrap() = 1;
                return *memo.get(&n).unwrap()
        }

        if n>2 && *memo.get(&n).unwrap()!= 0 {

                return *memo.get(&n).unwrap()

        }else {

                let y = fib(n-1,memo) + fib(n-2,memo);
                *memo.get_mut(&n).unwrap() = y;
                return *memo.get(&n).unwrap()
        }
}



fn main() {

    let mut memo = HashMap::new();

    let n = 5;

    for i in 1..n+1{
        memo.insert(i,0);
    }

    let x = fib(n,&mut memo);
    
    println!("{} element in Fibonacci is {}",n,x);

    for i in 1..n+1{
        println!("Hash element={},Key={}",memo.get(&i).unwrap(),i);
    }
    
}
     
```
