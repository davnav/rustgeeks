**Problem:(Medium)**

> create a a Struct with a value and function as a types inside. Call the function with parameter as the value type in the struct

struct Func_struct{
    val: i32
    func: address to the function
 }

> 



 
 

**Solution1**

```
  

struct FnStruct{
	value: i32,
	    f:Box<Fn(i32)->bool>,
}

impl FnStruct{
	fn new<F>(a: i32,f:F) -> Self

	where F:Fn(i32) -> bool+'static
		{

		FnStruct{ 
				value:a,
				f:Box::new(f)
		}
	}
}

	

fn condition(a:i32)->bool{
	a%2 == 0
}


fn main(){

	let f = condition;
	let fn1 = FnStruct::new(12,f);
	
	let fn2 = FnStruct::new(13,f);
	//println!("value is even={:?}",fn1.f);
	let foo1 = (fn1.f)(fn1.value);
	let foo2 = (fn2.f)(fn1.value);
	    
	
//	println!("{}",fn1.f.unwrap());
	println!("{},{}",foo1,foo2);
	
}	
	         
```
