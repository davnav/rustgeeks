**Problem:(Medium)**

> create a Tree data structure in Rust programming language and write functionality to read , insert and delete elements from Tree.

> 
Note : You can use below 3 pointer operators to allocate a memory space for Tree . Since Tree is recursive data type, we need to 
        use pointers 
       1. & borrow operator - reference to some place in memory, but it does not own the data it points to. As such, the lifetime 
          of the borrow depends on its owner.
       2.Box is a smart pointer with zero runtime overhead. It owns the data it points to. We call it smart because when it goes 
         out of scope, it will first drop the data it points to and then itself.
       3.Rc is another smart pointer. It's short for "reference-counting". It keeps track of the number of references to a data structure.
         As soon as the number of references is down to zero, it cleans up after itself

>hint: You can use 'push' method to add element into a Vector 


 
 

**Solution1**

```
  //main program 
  #[derive(Default)]
  #[derive(Debug)]
  pub struct Node{
	  value:i32,
	  left:Option<Box<Node>>,
	  right:Option<Box<Node>>,
  }

  impl Node{
	  pub fn new(new_value:i32) ->Box<Self>{
		  Box::new(Node{
			  value:new_value,
			  ..Default::default()			
		  })
	 }
	
	pub fn left(&mut self,new_value:i32){
		
		if self.left.is_none(){
			self.left = Some(Node::new(new_value));
		}
		
	pub fn right(&mut self,new_value:i32){
		
		if self.right.is_none(){
			self.right = Some(Node::new(new_value));
		}


	
	}

}



fn main(){

	let mut root = Node::new(100);

	root.left(50);
	root.right(30);
	println!("{:#?}",root);


}


     
```
