**Problem:(Meduim)**

> create a Merge Vector as sorted  for a vector which left side and right side of Mid point are sorted.

> input: Vector1 [2,13,14,15,6,7,19,20]
> output: print the Vector as [2,5,6,7,13,14,19,20]

Note : You might have noticed the vector is sorted upto Mid point ie v[3] = 15 and after Mid point too

>hint:
  1. You can use 'push' method to add element into a Vector 
  2. check first element in left half is less than first element in the right half and if its true , push the element 
   to a temporary vector and increment the left half index.
  3. else push the right half vector element to temporary vector and increment that right half index
  4. if its comeout without reaching the limit of any half , push the remaining elements of that half to temporary vector that 
    will be the higher elements.
  
  


 
 

**Solution1**

```
 /// main function - function call the "merge" function from the mid point
 
 fn main(){
 
 ///sample vector (vector is same as array - but its will be in heap memory)
 
        let mut v = vec![2,3,45,354,6,11,34,59];
/// you can try following vectors as well      let mut v = vec![2,5];
///the vector is sorted before and after mid point; 
///create function to merge the vector half those are in sorted order
        let n = v.len();
        let i = 0;

        let mid = n/2 ;
        
///if mid point zero means its a single element array

        if mid > 0 {
        
///call "merge" function with parameters 
///1. mutable reference to the vector
///2.left starting index
///3.left half ending index which "mid-1"
///4..starting point of right half index
///5.ending point of the right half is n-1, but we are passing n

///return a vector which is merged in a sorted manner

                v = merge(&mut v,i,mid-1,mid,n);
        };

        println!("{:?}",v);

}

///receive the index "usize" premitive type so that it can be used as index for vector

/// "merge" function will have parameters as
///1.mutable reference to a vector type
///2.left half index which should be mutable
///3.end limit for left half
///4.start index for right half which should be mutable as we are changing its value in the loop
///5.end limit for right half is n-1

/// return type a vector - Vec<i32>

fn merge(v:&mut Vec<i32>,mut i:usize,l:usize,mut j: usize, n:usize) -> Vec<i32>{

/// create a temporary vector which is empty

        let mut temp:Vec<i32> =[].to_vec()  ;
        
 /// loop through left half and right half elements to compare which ever lesser , push that to temporary vector      
        
        while i<=l && j < n {
        
           /// compare elements in left half and right half
           /// increment the index accordingly
 
                if v[i] < v[j]{
                        temp.push(v[i]);
                        i = i+1;
                }else{
                        temp.push(v[j]);
                        j = j+1;
                };
        }
        
 ///if its did not reach the left half limit, rest elements can be pushed  from left half as they will be higher elements
 
        while i<=l{
                temp.push(v[i]);
                i = i + 1;
        }
        
 ///if its did not reach the right half limit, rest elements can be pushed  from right half as they will be higher elements
       
       while j<n{
                temp.push(v[j]);
                j = j + 1;
        }
 /// return the "temp" vector
 
        temp


     
```
