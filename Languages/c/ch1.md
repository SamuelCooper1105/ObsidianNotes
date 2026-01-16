variables are intiiated with their type, and name and a value although this step is not neccesary.
a while loop is going to evaluate the condition as while as it is true.
division in c is truncated which means that if you have some value like 5/9, since the ratio of the two does not evaluate to an integer( a non fractional number), the decimal or frational porition of the number is disregarded. so 5/9 results to 0. even if you write it like 
``` 
	int x = 7;
	int y = x*(5/9); //y will be equivalent to 0
```
%d prints the integer as a decimal
%f prints a floating point number
%.2f specifies the amount of decimal places the float has
%o produces a octal number
%x produces a hex number
%s for a character string
%% for a percent%% 
getchar(); is a function that reads the first input chracter from a text stream.
putchar(c); is a function that printsa a character whenever it is called.

so like a simple program that looks like 
*read a character
while(character is not the end of file indicator)
	output the character
	read a character*
would like like this in c:
`#include <stdio.h>`
`int main(){`
	`int c ;`
	`c = getchar();`
	`while (c != EOF){`
		`putchar(c);`
		`c = getchar();`
		`}`
`}`


