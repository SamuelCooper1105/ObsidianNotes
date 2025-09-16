# Rust Notes

**These are going to be straight from the Rust Programming Book/Documentation so if you need any kind of guidance here it is!**

#### Chapter 1:

Alright so to install rust you're going to need to use the following command `curl --proto '=https' --tlsv1.2 https://sh.rustup.rs -sSf | sh`
This starts the install and downloads the most recent, stable version of Rust. You also need a linker( tool that, you guessed it, links your compiled files together into one executable.)

`rustc --version` returns Rust Version currently installed. `rustup update` updates rust. `rustup doc` returns the documentation to look over. If you need to work offline then you can download a large porition of rust dependencies using the following commands.
`cargo new get-dependencies
cd get-dependencies
cargo add rand@0.8.5 trpl@0.2.0` These will download the dependencies needed. However the dependencies added here are what are used in this guide so keep that in mind for future reference. You can also use the command flag ` --offline` when you run `cargo`. 

to compile and run a file use teh following code ` rustc main.rs( when your file is called main) /nl ./main` 

your typical hello, world program in rust looks like the following. 
`fn main(){
println!("Helllo, World");
}` 
Now here are a few definitions, 
fn: this denotes a function being declared.
println!: THis is a macro that prints an input string to the screen or terminal.
A macro in rust is slightly different then a function this can be further explained in the [[Chapter 20:]] Notes. Before running a Rust Program it must be compiled, you can compile a program by using the `rustc` command followed by the name of your file with its .rs identifier. 

cargo is the build system and package manager for Rust. Can handle building the code, downloading libraries, should be installed with the standard Rust application. 

#### Chapter 2:

use std::io: this is the declaration to use the standard library input/output library. 
There is a set of items included in all Rust projects that is called the prelude. let: declares a variable, mut: introduces mutability to an object. String::new: is how we create a new instance of a string type. :: indicates that whatever follows is a function of whatever preceded ::. 
.read_line is the standard method to get input from the user. it takes an argument that we need to make sure is mutable, and a reference which we can declare using &. [[reference]]. This also returns a Result value, which is an enumuration. Result's variants are Ok and Err, these can be handled by .expect()
.expect() is a method that checks Result's value, if Err is the type then .expect() crashes the program and returns the error message that .expect() takes as an argument. if Result's type is Ok then .expect will return the value that Ok holds. 
this is kind of a work around for errors, normally we would just write error handling code, but this allows us to kind of avoid any of that, and provides a wrap around. 
So atp the code should be displaying 
'Guess the Number!
Please input your guess:
{your guess}
You guessed: {you guess}`

So a crate is a colection of Rust soruce code files, the projecty we've been building is a binary crate. which is a executable. The Rand crate is a library crate that contains code that is used for other code files. This is where Cargo really comes into play, we need to modify the cargo.toml file to add the crate as a dependency. make sure to use the proper version number as well for this. 
	rand::Rng; : this trait(Rng) defiens several methods that the random number generator project will need to use. rand::thread_rng: provides a random number generator. This generator is local to the system and seeded by the operating system. gen_range(): takes a range as an argument, input as start..=end, and then generates a random number within that range. 
Now obviously you're not going to have a guide on how to use each of these things to the best of their ability so every crate has documentation included with instructions on how to use it. you can open this documentation with `cargo doc --open` 
now we can focus on comparing the values. to do this we can use a crate called cmp, from this crate we are going to use a type called Ordering, which is an enumeration and has the variants `less, greater, equal` cmp compares two different values, we'll call it in this scope as follows,
` match guess.cmp(&secret_number){
	Ordering::Less => println!("Too small."),
	Ordering::Greater=>println!("Too big"),
	Ordering::Equal=> println!("You win."),
}`

Basically what this is doing is comparing secret number to guess, which then based off the compare result calls the appropriate 'arm' of match. SO in a match, there are arms, and each arm has a pattern that we can compare with. Also match will return the first correct value that gets returned. However if you run this code, you'll get an error because you are trying to compare a string, guess, to a number, secret_number. Rust has type inference so it will make assumptions on what a variables' type should be. 
Alright so how can we fix this? we can use something called shadowing, which is where we can reuse a variable name and shadow the value contained within.
we can accomplish this with the line `let guess: u32 = guess.trim().parse().expect("please type a number");`
guess is the original variable in this context, trim(): is a method taht will get rid of any white space at the beginning or the end of the string, this is needed to convert a string to a u32 integer. parse() is the method that actually converts a string to a integer. we can specify this by specifying what type we want to convert to with the let guess: u32 bit of the line. Since Rust has type inference the code will assume that since we are comparing a u32 integer to another number then that value must also be a u32 integer. so since parse is converting a string to another value, an integer in this case. we will need to account for some kind of potential errors especially if our string contains a value like, "%^#", obviously we can't just convert the value into a number meaningfully. because of this parse also contains a Result type. If parse cannot return a number then it will return an Err type.

loop: this starts an infinite loop.
if you move most of the main logic within the loop{}, then you can create a game where the user can continuously input guesses. The only problem here is that, since this an infinite loop the only way to break the loop is too input some answer that is not a number, like 'yes'. Obviously this is just a practice program but still we want this to be robust as possible.
so what if we want the program to quit after the user guess correctly? all we need to do is insert a break line in the equal logic as follows,
` Ordering::Equal =>{
	println!("you win!");
	break;
	}`
IF the user wins then the program will break the loop and the program.
so we can handle this with the keyword continue, we just need to change the Err handling when we convert the String. The code will appear as follows,
`let guess; u32 = match guess.trim().parse(){Ok(num) => num, Err(_) => continue,};` 

By hcaning expect to a match expression we can effectively just check the enumrations of prase(), so if Ok is a num then the code continues, and if Err contains any value, we can use _ as a catchall for this purpose, this then goes to the continue command which tells the code to begin the next iteration of the loop which will then prompt the user fora another set of input. 

Here is the finished code for Chapter 2: 
` 	use std::cmp::Ordering;
	use std::io;

	use rand::io;

	fn main(){
  		println!("Guess the Number!");

  		let secret_number = rand::thread_rng().gen_length(1..=100);

  		loop{
    		println!("Please input your guess.');
  
    		let mut guess = String::new();

    		io::stdin(),read_line(&mut guess).expect("Failed to read line");
	  		let guess: u32 = match guess.trim().parse(){ Ok(num) =>num,Err(_)=> continue,};
    		println!("You guessed: { guess}");

    		match guess.cmp(&secret_number){
     			Ordering::Less=>println!("too small!"),
      			ORdering::Greater => println!("too big!"),
      			Ordering::EQual =>{
       				println!("you win!");
        			break;
      			}
    		}
  		}
	}
` 

#### Chapter 3:



