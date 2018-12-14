**Problem:(Medium)- Rust programming language**

>**How to cut the rod of length n with given price Vector for getting maximum profit using Rust programming language**

> input: Price Vector [3,5,8,9,10,17,17,20]
         length       [1,2,3,4,5,  6, 7,8 ]
 > output: output will be 24 
 
 ( ie: it should cut at length 6 and 2 to get maximum profit ( 8*(1*3) = 24 ))



We need to find maximum of 'price at cutting each length + maximum Profit getting when excluding decided cutting length) 

ie : 

rod length =8 

> **MAX ( price[0] +cutRod_maxProfit(8-0-1),price[1]+cutRod_maxProfit(8-1-1),price[2]+cutRod_maxProfit(8-2-1)....
        ...price[7]+cutRod_maxProfit(0) )**
```	
If we decided to go with price[0] means we decided to cut one piece with length 1 ,
then only option for us is to think of how to get maximum profit from remain length 7 which is 
can be found from cutrod_maxprofit(7,price) 
```
Note : Vector index start from 0 to n-1, so price[0] = 1
     : Vector and Arrays are different in Rust on how/where data stores
	
**Please fill rest of the coloumn,you will see a pattern
eg: if you see cutting rod of length 3 , with piece of length 2, the profit is 8
    but max profit of cutting rod of length 3, with piece of {1,2} is 9 because with piece of length 1 maxprofit is 9
    since 9 > 8 , just put the greater that value (from above coloumn) to that coloumn**
    
    

            
 |    | 1  | 2 |  3  | 4  | 5  | 6  |  7|  8|
 |----|----|----|----|----|----|----|---|---|
 |  1 | 3(max profitfor length 1 with 1 length piece)  | 6 | 9  | 12 | 15 | 18 | 21 | 24(max profitfor length 1 with length piece{1})|
 |  2 | 3(max profitfor length 1 with length piece{1,2}) | 6  | 9 (max profitfor length 3 with length piece{1,2}) |  |
 |  3 |  |  |  |  |  |
 |  4 |  |  |  |  |  |
 |  5 |  |  |  |  |  | 
 
 
 
 

**Solution1 - Using Recursion**

```
 
//main program
fn main(){

//price vector(array) 
	let price = vec![3,5,8,9,10,17,17,20];
//length at which road can be cut, is from 1 to 8.
	let n =  price.len();
//calling functio,n to cut the road of length 8 which return maximum profit 
	let max_val = cutrod_with_maxprofit(n,&price);
	
	println!("{}",max_val);
}

// function to find maximum of passed parameters
//function return an integer
//its comparing maximum value so far with current max value

fn max(max:i32,curr_val:i32) -> i32{


	println!("max={},curr_val={}",max,curr_val);
	
	if max > curr_val{
		max
	}else{

		curr_val
	}

	//println!("max={},curr_val={},max,curr_val");

}


//accept parameters with length n which of type as we are using it as vector index
//and vectorarray passed with borrow reference

fn cutrod_with_maxprofit(n:usize,price:&Vec<i32>) -> i32{	

	let mut max_val = 0;
//base condition for recursion	
//rod of length =0 or less the cut is impossible,so return 0
	if n <= 0{
		return 0
	}
// finding each length cut maximum profit
//so i is the decided length to cut
// if we decided to go with price[0] means we decided to cut one piece with length 1 ,
//then only option for us is to think of how to get maximum profit from remain length 7 which is 
//can be found from cutrod_maxprofit(7,price) 
	for i in 0..n{
		 println!("i={},n={},max_val={}",i,n,max_val);
		 max_val = max(max_val,price[i]+cut_rod(n-i-1,price));

		}
//return the max_val calculated for passed length for each recursion
	max_val

}



 
 
```
