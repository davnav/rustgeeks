**Problem:(Medium)- Rust programming language**

>**How to cut the rod of length n with given price Vector for getting maximum profit using Rust programming language- Dynamic Programming **

> input: Price Vector [3,5,8,9,10,17,17,20]
         length       [1,2,3,4,5,  6, 7,8 ]
 >Dynamic Programming - is an approch for divide and conquor problems.Here you will be storing the values already find out in the earlier iternation or calculation
 >
 >output: output will be 24 
 
 ( ie: it should cut at length 1 of 8 pieces  to get maximum profit ( 8*(3) = 24 ))



We need to find maximum of 'price at cutting each length + maximum Profit getting when excluding decided cutting length) 

ie : rod length =8 

> **MAX ( price[0] +cutRod_maxProfit(8-0-1),price[1]+cutRod_maxProfit(8-1-1),price[2]+cutRod_maxProfit(8-2-1)....
        ...price[7]+cutRod_maxProfit(0) )**
```	

If we decided to go with price[0] means we decided to cut one piece with length 1 ,
then only option for us is to think of how to get maximum profit from remain length 7 which is 
can be found from cutrod_maxprofit(7,price)

store the values found each call for cutRod_maxProfit in another vector

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
 
 
 
 

**Solution1 - Using Dynamic Programming**

```
 fn main(){

	//price vector has price for each length 1,2,3..8
	let price = vec![3,5,8,9,10,17,17,20];

	let n =  price.len();

	//the vector which stored the maximum profit for each length
	let mut maxvec = [].to_vec();


	let max_val = cutrod_maxprofit(n,&price,&mut maxvec);
	
	println!("{}",max_val);
}

//max function to find the maximum of passed values and return the maximum
fn max(max:i32,curr_val:i32) -> i32{


	println!("max={},curr_val={}",max,curr_val);
	
	if max > curr_val{
		max
	}else{

		curr_val
	}


}


fn cutrod_maxprofit(n:usize,price:&Vec<i32>,maxvec:&mut Vec<i32>) -> i32{	

	let mut max_val = 0;
	if n <= 0{
		return 0
	}

//check the "maxvec" stored the max value for the length "n" which might be stored in maxvec[n-1]
	match  maxvec.get(n-1) != None {
		 true  =>  { maxvec[n-1]    },
	
		 false  =>  {


				for i in 0..n{

//call the max function to find the maximum of "maxval"
			 		max_val = max(max_val,price[i]+cutrod_maxprofit(n-i-1,price,maxvec));
				}
				maxvec.push(max_val);
				max_val
			} 

	}

}


	


 
 
```
