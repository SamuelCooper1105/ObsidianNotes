# Rust Notes

**These are going to be straight from the Rust Programming Book/Documentation so if you need any kind of guidance here it is!**

#### Chapter 1:

Alright so to install rust you're going to need to use the following command `curl --proto '=https' --tlsv1.2 https://sh.rustup.rs -sSf | sh`
This starts the install and downloads the most recent, stable version of Rust. You also need a linker( tool that, you guessed it, links your compiled files together into one executable.)

'rustc --version` returns Rust Version currently installed. `rustup update` updates rust. `rustup doc` returns the documentation to look over. If you need to work offline then you can download a large porition of rust dependencies using the following commands.
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
