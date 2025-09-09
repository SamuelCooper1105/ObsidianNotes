# CINCI PROJECT

### Definitions:

- TON: Generate on-delay: Starts when the input(IN) changes from a 0 to 1, or a positive singal edge, the programmed time then starts from teh designated time as set in the PT input, once the time has elapsed the output Q will be changed to a 1. Q will stay as 1 until the input changes back to a 0. When the singal at teh start of the input changes from a 1 to a 0, then Q is reset. Current time can be read from ET and the value will reset when IN changes to 0.
- 


### Code: 

Alright so we start with the Main block obviously, which calls the System function first. The system function starts with a nomrally closed circuit( SystemStatus. one_second_flash) which then feeds into a TON circuit, where a timer of 1 second is set. the "One_second_tMR".Q output is then written to, which then consequently sets the one_second_ flash.
This process is then repeated in the second branch of network 1. A lot of what seems t o be going on here in this function, is setting a timer and setting a light to go off, which signals the status of the system.




