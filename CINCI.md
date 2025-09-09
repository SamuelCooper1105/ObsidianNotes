# CINCI PROJECT

### Definitions:

- TON: Generate on-delay: Starts when the input(IN) changes from a 0 to 1, or a positive singal edge, the programmed time then starts from teh designated time as set in the PT input, once the time has elapsed the output Q will be changed to a 1. Q will stay as 1 until the input changes back to a 0. When the singal at teh start of the input changes from a 1 to a 0, then Q is reset. Current time can be read from ET and the value will reset when IN changes to 0.


### Code: 

Alright so we start with the Main block obviously, which calls the System function first. The system function starts with a nomrally closed circuit( SystemStatus. one_second_flash

