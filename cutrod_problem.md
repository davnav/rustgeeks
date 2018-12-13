**Problem:(Medium)**

>How to cut the rod of length n with given price Vector

> input: Price Vector [3,5,8,9,10,17,17,20]
         length       [1,2,3,4,5,  6, 7,8 ]
 > output: output will be 22

Note : Vector and Arrays are different in Rust on how/where data stores

>If you are not sure how insert sorting algorithm works :
  Clue: 1. One loop read the elements of the Vector from left to right from second element onwards to last element.
        2. from the first loop point element ( we can call it as Key) , we will compare from right to left and insert the key in the correct position
            
 |    | 1  | 2 |  3  | 4  | 5  | 6  |  7|  8|
 |----|----|----|----|----|----|----|---|---|
 |  1 | 3  | 6 | 9  | 12 | 15 | 18 | 21 | 24|
 |  2 | 3 | 6  | 9  |  |
 |  3 |  |  |  |  |  |
 |  4 |  |  |  |  |  |
 |  5 |  |  |  |  |  | 
 
 
 
 

**Solution1**

```
 

fn main(){

	let price = vec![3,5,8,9,10,17,17,20];

	let n =  price.len();

	let max_val = cut_rod(n,&price);
	
	println!("{}",max_val);
}

fn max(max:i32,curr_val:i32) -> i32{


	println!("max={},curr_val={}",max,curr_val);
	
	if max > curr_val{
		max
	}else{

		curr_val
	}

	//println!("max={},curr_val={},max,curr_val");

}



fn cut_rod(n:usize,price:&Vec<i32>) -> i32{	

	let mut max_val = 0;
	if n <= 0{
		return 0
	}
	
	for i in 1..n{
		 println!("i={},n={},max_val={}",i,n,max_val);
		 max_val = max(max_val,price[i]+cut_rod(n-i-1,price));
		
	//println!("n={},max_val={},i={},n-i-1 = {}",n,max_val,i,n-i-1);

		}
	
//	println!("n={},max_val={},",n,max_val);
	
//	println!("n={},max_val={},i={}",n,max_val,i);
	max_val

}



 
 
```
