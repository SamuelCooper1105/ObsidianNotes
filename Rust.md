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

By hcaning expect to a match expression we can effectively just check the enumrations of parse(), so if Ok is a num then the code continues, and if Err contains any value, we can use _ as a catchall for this purpose, this then goes to the continue command which tells the code to begin the next iteration of the loop which will then prompt the user fora another set of input. 

Here is the finished code for Chapter 2: 

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


#### Chapter 3:

So in Rust variables are immutable by default. the `mut` keyword allows for us to make a variable mutable.
##### Constants
Constants are values that are bound to a name and are not allowed to change under any circumstances, they remain immutable throughtout the scope of the code. declared using the `const` keyword, the type of data the const is must also be declared. The naming convention for constants is to use all upper case, with words seperated by underscores. 
##### Shadowing
Shadowing is when we create a new variable using a prexisting name for a variable. The second value declared overshadows the first variable named, as long as it remains within the scope it is declared within. There is no need to use `mut` within this context, as by shadowing a variable you are effectively creating a new variable, you're just sharing the name and giving priority of the name to the 'new' variable. For example if you declared a value and made it mutable, but then tried to change the data type you would get a compile error as you can not mutate a variable's data type. 

##### Data Types: 
Rust is statically typed so you should know the type of all variables at run time. The compiler can usally infer what data type we want to use at compile time, but there are times where multiple data types could be possible. These data types include Scalar values, these represent a single value and include integers, floating points, booleans, and characters. An integer is a number with no fractional component, there are signed (i) and unsigned (u) integers which refer to if they can support a negative number or not. 



let f: bool = true
let t: bool = false

Compound Types:

These are types of data that can contain other data types. In Rust the main kinds of compound types are the tuple and the array. The tuple is a general way of grouping values together regardless of their data type. Tuples like arrays have a fixed size and can not grow or shrink.
They are declared as follows.
`fn main(){
	let tup: ( i32, f63, bool) = ( 101, 56.78, true);
}`

you may use pattern matching to destructure a tuple and fetch individual elements, like as follows ` let (x,y,z) = tup;` it is also possible to access individual elemetns of a tuple by refrecning the index using a period, this can be done as follows`let one_oh_one = tup.0` this would assign the value 101 to the variable one_oh_one. Now a tuple with no values is called a unit and this is the default return type for a function if no return type is specified. 

The array is another compound data type except an array may only contain values of the same data type. They are declared as follows, `let arr = [1,2,3,4,5];` they are allocated on the stack, and will always have a fixed size. A vector is also included within Rust but is not within the standard library. you can decide what the size and data type of an array will be by declaring it as follows, ` let arr[u32; 5] =[1,2,3,4,5]; `. To intitlize an array with a set value in each indice, you will need to declare it as follows, `let arr = [3;5];`. You can access elements just like you would in c/c++ or python. 


##### Functions:

a function is declared in rRust using the `fn` keyword and followed by a set of parthensizes that can contain the argument for the function and then a set of curly brackets, to contain the code body of the function. You can specify arguments as follows, ` fn my_function ( x: i32) {}`, x is the argument or parameter and then we specifiy what type x has to be in order to be passed as a proper argument. Functions in Rust are made up of statements(instruction that performs an action and returns no value, i.e. `let x =5;`) 

alright so expressions, so rust is an expression based language whatever the fuck that means, but basically when you create a variable its a statement, it doesn't return anything so its a statement. as in line with this llogic the way you can assign two variables teh same value like in c/c++, ` int x = y = 3` we cannot do `let x = ( let y = 5)` in rust cuz we are not returning anything to bind to x. basically an expression evaluates to a value. so 5 +6 is an expression as it evalutes to 11, whereas let x =11 doesn't evaluate to anything cuz its just a vriable assignment. 
