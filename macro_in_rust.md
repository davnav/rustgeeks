# Macros in Rust programming 

Macros are a powerful feature in Rust programming language. Since it is compiled to syntax tree rather than string pre-processing, it has advantages over other language's macro.

When I started with Rust macro, it was taking me to a new programming style altogether. You can easily convert the reusable part of your program to macros. It is called  **meta programming .**

## Declarative Macros 

we are going to discuss only this type macro creation in this post. 

Macros will try to match pattern  passed , if it succeed the match proceed with code defined in curly brackets.

```
How to start with Rust macro: 

macro_rules! macroname{
	() => { }
}
```
```
macro_rules! = is the macro using in rust for creating 

'macro_name' =  is the name you want to be for the macro which can be invoked by *'macro_name!'*

```
```
( ) => {}

 () is the sytax for pattern matching 
 {} is the place we need to enter the code to exceuted.
 
```

-   `ident`: an identifier. Examples:  `x`;  `foo`.
-   `path`: a qualified name. Example:  `T::SpecialA`.
-   `expr`: an expression. Examples:  `2 + 2`;  `if true { 1 } else { 2 }`;  `f(42)`.
-   `ty`: a type. Examples:  `i32`;  `Vec<(char, String)>`;  `&T`.
-   `pat`: a pattern. Examples:  `Some(t)`;  `(17, 'a')`;  `_`.
-   `stmt`: a single statement. Example:  `let x = 3`.
-   `block`: a brace-delimited sequence of statements. Example:  `{ log(error, "hi"); return 12; }`.
-   `item`: an  [item](https://doc.rust-lang.org/1.6.0/reference.html#items). Examples:  `fn foo() { }`;  `struct Bar;`.
-   `meta`: a "meta item", as found in attributes. Example:  `cfg(target_os = "windows")`.
-   `tt`: a single token tree.


<a href="https://www.blogger.com/goog_2029802335"><br /></a>
<span style="background-color: #e1e1db; font-family: &quot;open sans&quot; , sans-serif; white-space: pre;"><a href="https://play.rust-lang.org/?version=stable&amp;mode=debug&amp;edition=2018&amp;gist=4c0702ac8375cf375a432612b49bc390">Macro custom print</a>
```
macro_rules! print_new{
//in this example we are passing the expression which has only one value which will be stored in $x
 
 //we need to define name and designator 
 // here **$x** is Name or variable
 // **expr** is type to match for name
    ($x:expr) => (
        println!("value={}",$x);
    )
}


fn main() {
    print_new!(5);
}
```
In rust almost everything is expression .In the above example we passed the 'expr' as 5  where 5 designated as name


<br />
example 2:<br />
In this example we formatted the pattern as x=> 10+10 which equivalent to x=>$x:expr  where $x get the value of 20
<br>
<a href="https://play.rust-lang.org/?version=stable&amp;mode=debug&amp;edition=2018&amp;gist=891d6b121176dec7081e37791cff7598">macro expression passing</a><br />
<br />
<br />
example3:<br />
Here we are passing function name as Identifer to generate/define a function
<br />
<a href="https://play.rust-lang.org/?version=stable&amp;mode=debug&amp;edition=2018&amp;gist=3a442f981feb53073f8ab90cf1dd33a5">macro - building function</a><br />
<br />
example4:<br />
<br />
<a href="https://play.rust-lang.org/?version=stable&amp;mode=debug&amp;edition=2018&amp;gist=14ca32d36928f2e366b7951182dffbea">macro -apply function to a range of numbers</a><br />
<br />
<br />
example5:<br />
<a href="https://www.blogger.com/goog_975707039"><br /></a>
<span style="background-color: #e1e1db; font-family: &quot;open sans&quot; , sans-serif; white-space: pre;"><a href="https://play.rust-lang.org/?version=stable&amp;mode=debug&amp;edition=2018&amp;gist=e4f09f77d1f86c29dea4bbbc590d8c9d">macro with pass dentifiers(variables)</a></span>



**Reference** 

https://words.steveklabnik.com/an-overview-of-macros-in-rust

https://danielkeep.github.io/tlborm/book/index.html

https://danielkeep.github.io/practical-intro-to-macros.html
