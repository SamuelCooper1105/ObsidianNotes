# Rust Notes

**These are going to be straight from the Rust Programming Book/Documentation so if you need any kind of guidance here it is!**

#### Chapter 1:

Alright so to install rust you're going to need to use the following command `curl --proto '=https' --tlsv1.2 https://sh.rustup.rs -sSf | sh`
This starts the install and downloads the most recent, stable version of Rust. You also need a linker( tool that, you guessed it, links your compiled files together into one executable.)

`rustc --version` returns Rust Version currently installed. `rustup update` updates rust. `rustup doc` returns the documentation to look over. If you need to work offline then you can download a large porition of rust dependencies using the following commands.
`cargo new get-dependencies
cd get-dependencies
cargo add rand@0.8.5 trpl@0.2.0` These will download the dependencies needed. However the depenendcies addded here are what are used in this guide so keep that in mind for future reference. You can also use the command flag ` --offline` when you run `cargo`. 

to compile and run a file use teh following code ` rustc main.rs( when your file is called main) /nl ./main` 

your typical hello, world program in rust looks like the following. 
`fn main(){
println!("Helllo, World");
}` 
Now here are a few definitions, 
fn: this denotes a function being declared.
println!: THis is a macro that prints an input string to teh screen or terminal.
A macro in rust is slightly different then a function this can be further explained in the [[Chapter 20:]] Notes. Before running a Rust Program it must be compiled, you can compile a program by using the `rustc` command followed by the name of your file with its .rs identifier. 

cargo is the build system and package manager for Rust. Can handle building the code, downloading libraries, should be installed with the standard Rust application. 

#### Chapter 2:

use std::io: this is the declration to use the standard library input/output library. 
There is a set of items included in all Rust projects that is called the prelude. let: delcares a variable, mut: introduces mutability to an object. String::new: is how we create a new instance of a string type. :: indicates that whatever follows is a function of whatever preceded ::. 
.read_line is the standard method to get input from the user. it takes an argument that we need to make sure is mutable, and a reference which we can declare using &. [[reference]]. This also returns a Result value, which is an enumuration. Result's variants are Ok and Err, these can be handled by .expect()
.expect() is a method that checks Result's value, if Err is the type then .expect() crashes the program and returns the error message that .expect() takes as an argument. if Result's type is Ok then .expect will return the value that Ok holds. 
.expect() 
