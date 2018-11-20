**Problem:**

>Create a program to find a largest String from from the two Strings given

>String is handled differently in Rust programming language. Strings need to be handled carefully, otherwise it cause segmenation 
fault in C like programming languages.So it is necessary to read 
<a href="https://doc.rust-lang.org/book/second-edition/ch08-02-strings.html">Rust documentation</a>


**Solution**

```
  //function to get the largest string

  fn largeststring<'a>(str1:&'a str,str2:&'a str) -> &'a str{
        if    str1.len() > str2.len(){ str1 }
        else if    str1.len() < str2.len(){  str2 }
        else { "Both Strings are in the same length" }
}


//main function

fn main(){

        //String1 which is stored in the heap

        let str1 = String::from("Helloasasa");

        //String stored as slice.. means string in the stack memory
        let str2 = "worldasd";

        let str = largeststring(str1.as_str(),str2);

        println!("{}",str);

}
~          
```


