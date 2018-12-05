**Problem:(Medium)**

> create a merge sort program in Rust .

> input: Vector1 [2,7,19,11,20,33,4]
> output: print the Vector as [2,4,7,11,19,20]

Note : Vector and Arrays are different in Rust on how/where data stores

>hint: You can use 'push' method to add element into a Vector<br>
>      You can use recursion as we need to use "divide and conquer" idea<br>
>      You can make use of previous problem( merge sorted vectors)  <a href="rust_merge_sortedvectors.html">merge sorted vectors</a>



 
 

**Solution1**

```
 
fn main(){
	let mut v = vec![2,56,12,11,34,59,12,2342];
	let n = v.len() as usize ;
	let i = 0;

	mergesort(&mut v,i,n-1);
	
	println!("{:?}",v);

}

fn mergesort(v:&mut Vec<i32>,i:usize,j:usize){
	
	let mid = (i+j)/2;

	if  i<j  {
//		let mid = (i+j)/2;
		println!("mid={},i={},j={}",mid,i,j);
		mergesort(v,i,mid);
		mergesort(v,mid+1,j);
		
		merge(v,i,mid,mid+1,j);
	}

}

		
fn merge(v:&mut Vec<i32>,mut left_half_lower:usize,left_half_upper:usize,mut right_half_lower: usize, right_half_upper:usize){

	let mut temp:Vec<i32> =[].to_vec()  ;
	let mut i1 = left_half_lower;
	let j2 = right_half_upper;

	while left_half_lower <= left_half_upper && right_half_lower <= right_half_upper {
		if v[left_half_lower] < v[right_half_lower]{
			temp.push(v[left_half_lower]);
			left_half_lower = left_half_lower + 1;
		}else{
		   	temp.push(v[right_half_lower]);
		 	right_half_lower = right_half_lower + 1;
		};
	}
	while left_half_lower <= left_half_upper{
		temp.push(v[left_half_lower]);
		left_half_lower = left_half_lower + 1;
	}
	while right_half_lower <= right_half_upper {
		temp.push(v[right_half_lower]);
		right_half_lower = right_half_lower + 1;
	}

	println!("i1={},j2={}",i1,j2);

//	while left_lower_limit <= right_upper_limit && j < temp.len()  {
	for e in &temp {
			if i1 <= j2 {
				v[i1] = *e;
				i1  = i1 + 1;
			}
	}

	
	
	//println!("left_lower_limit ={}",left_lower_limit);
	//println!("right_upper_limit={}",right_lower_limit);
	println!("temp={:?}",temp);
		
	println!("v after merge {:?}",v);

}






     
```
