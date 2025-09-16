# Rockwell Notes


#### Tasks: 
A task is how the Logix controller allows you to schedule and prioritize programs based on criteria you set forth. This allows for the user to allocate processing time of the controller for specific tasks. So a controller allocates its processing time among the separate operations being executed in the application. 
- A controller can only execute one task at a time
- A task can interrupt another and take control.
- in any task several programs can be used, but only one can execute
- You can display task in the controller or logical organizer
So a project may have 32 tasks each of which can have 1000 programs each. Each task has a separate priority level, this is how the CPu decides what tasks to execute priority levels are organized from 1, the highest, to 15, the lowest. Rememver the Continous Task will always have teh lowest priority of any task. 
A continuous task runs in the background and has the lowest priority, any CPU spare time that used for other operations is used to execute any programs in a continuous task. There may only be ONE continuous task in a project.
A periodic task performs a function at a set interval, whenever time for a periodic task expires. The task will interrupt any lower priority tasks, execute itself and then return to whatever task it interrupted and continue that task from where it left off. 
An Event Task, performs a function only when a specific event( trigger) occurs. The trigger of the event can either be a module input data change, a tag trigger, an EVENT instruction, an Axis trigger or even a motion event trigger. 


#### Programs: 
so a program contains data and logic, alongside Routiens to contain executable code. Each program is going to contain local tags, parameters, a main executable routine, and an optional fault routine, along with other standard routines. The programs within a task execute from first to last, we can have programs that are not scheduled are referred to as unscheduled programs. 

#### Routines:

A routine is a set of logic instructions that are written in one programming language. Each program has a main routine, this is the first to execute itself when the program is called. You can call other routines with a Jump to Subroutine, or you can create a program fault routine which the program will call if there is an instruction-execution fault in the routines within a program. 

#### Tags:

Tags are the specified data within the controller memory. These are identified by an alpha-numeric name. These can span from a single bit to large data structures. There are local tags and then controller tags.
- A local tag can be accessed from just within a specific program where they 'reside', same thing as an encapsulated variable
- A controller tag can be accessed from anywhere within the project. 

#### Parameters:

A parameter may be accessed from within the program where they are located. They can also be accessed from outside the program using connections or a special type of addressing that includes the program name. Parameters refer to data that is contained in controller memory that can be accessed from within the program where the data is associated, outside of the program when a connection is present, and can be accessed outside the program with special addressing. 

#### Ladder Logic:

Rungs: Rungs are read from top to bottom and from left to right. Each rung in the logic MUST contain an output. 
Bit-Level Instructions: a bit level instruction is assigned a tag with a BOOL data type. 
Inputs/Conditions: Input instructions are conditions for outputs to happen. i.e when creating a if then statement, the input would be your IF.
Examine if Closed: this is a Boolean instruction that executes when the tag tied to the instruction is a 1 value. 
Examine if Open: This is a Boolean instruction that executes when the tag tied to the instruction is false, or 0.
Outputs: This is what happens when a circuit is complete, the THEN in a loop.
Output Energize: Writes a 1 to its associated tag if there is logical continuity and writes a 0 if not. 

A backplane is a hardware piece that contains a proprietary communication network for controllers and hardware modules. as well as distributing power across those modules and controllers. 

Electronic Keying: This is a process that compares the device that is defined in the project to he installed device. The purpose of this feature is to reduce the possibility that a wrong device is being used in a control system. If this fails, a fault will occur. You can either use compatible module, which is where the installed devices accepts the key of the device that is defined in the project when the installed device can emulate the defined device, With compatible mode, you can usually replace a device with another device that has the following characteristics: Same catalog number, same or higher major revision, or a minor revision as follows: if the major revision is the same, then the minor revision must be the same or higher. If the major revision is higher, then the minor revision can be any number. You can also disable keying , this way communication with that device even if it is not the same type as defined in the project. Finally there is exact match, which is where all keying attributes must be exactly the same to establish communication. if any attribute does not match exactly then communication will not occur. 

#### Atomic Data Types:

An atomic Data type is the most base level data types in an application. In ladder logic these are as follows
- BOOL: Represents a single bit of memory, so it can only hold one of two values, 1 or 0. Can also be represented as true or false.
- SINT: This is a short integer and represent a single byte of memory, this can contain decimal values from -128-127 as it is a signed numer that uses two's compliment. 
- INT: a integer that uses 2 bytes of memory. Also uses two's compliment, and thus can represent decimal values raning from -32,768 to 32767.
- DINT: an integer type that uses 4 bytes of singen mory and can represent decimal values from -2147483648 to 2147483647
- REAL: a real data type reperenst s4 bytes worth of floating point memory, the first 22 bits are representive of the fraction part of a number and bits 23-30 represent teh exponent level with the 31st bit representing the sign.
Each atomic data type consumes 32 bits worth of memory, so when youre using data type smaller then a DINT or REAL, then implmennting arrays is good practice.

#### Hardware Tags

hardware tags are automatically created by rockwell software when you add hardware. These are module defined data types that are related to a specfic module. we should be able to connect hardware tags to parameters so that the program can connect to the hardware and modify the external values of that hardware. The data types in the tags and the parameters must be the same. 

InOut Parameters: an inout parameter is a special usage program parameter that represents areference to data that can be used as both an input and an output during the execution of a program. since these are passed by reference rathter then by value then thet are just a pointer as thus resemeble the bahvior of an alias tag. However it is possible for an InOut parameter value to change during the execution of a program. dpending on thet ask at hand this behavior could be necessary. InOut parameters can only support one onnection, you cannot configure connection to any member of the InOut parameters. An inOut paramter can only be connected to an output paramter if the inout paramter is configured as a constant. Inout paramters are passed by reference which means they are pointing ot he base tage, in other words when an inOut parameter is used in logic, the curret value of the oparamter connected to the InOut paramter is used. Connection to InOut paramters cannot be changed online, unless using the Partial Import online functionality.
