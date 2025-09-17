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
so a program contains data and logic, alongside Routines to contain executable code. Each program is going to contain local tags, parameters, a main executable routine, and an optional fault routine, along with other standard routines. The programs within a task execute from first to last, we can have programs that are not scheduled are referred to as unscheduled programs. 

#### Routines:

A routine is a set of logic instructions that are written in one programming language. Each program has a main routine, this is the first to execute itself when the program is called. You can call other routines with a Jump to Subroutine, or you can create a program fault routine which the program will call if there is an instruction-execution fault in the routines within a program. 

##### Creating a Routine:

a routine is a set of logic instructions in one programming language such as LAD. ROutiens allow for executable code in the project. A routine is similar o a program gile or subroutine in a PLC or SLC processor. Each program has a main routine, the main routine is the first routine to execute when the controller triggers the associated task and calls the associated program. use logic such as the JUMP to SUBROUTINE instruction to call other routines, You may also sepfict an optional program fault routinem which is executed whenever a routine within the associated program eencoutuners an instruction execution fault. 


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
- SINT: This is a short integer and represent a single byte of memory, this can contain decimal values from -128-127 as it is a signed number that uses two's compliment. 
- INT: a integer that uses 2 bytes of memory. Also uses two's compliment, and thus can represent decimal values ranging from -32,768 to 32767.
- DINT: an integer type that uses 4 bytes of signed memory and can represent decimal values from -2147483648 to 2147483647
- REAL: a real data type represents s4 bytes worth of floating point memory, the first 22 bits are representative of the fraction part of a number and bits 23-30 represent the exponent level with the 31st bit representing the sign.
Each atomic data type consumes 32 bits worth of memory, so when you're using data type smaller then a DINT or REAL, then implementing arrays is good practice.


#### Hardware Tags

hardware tags are automatically created by rockwell software when you add hardware. These are module defined data types that are related to a specific module. we should be able to connect hardware tags to parameters so that the program can connect to the hardware and modify the external values of that hardware. The data types in the tags and the parameters must be the same. 

InOut Parameters: an InOut parameter is a special usage program parameter that represents a reference to data that can be used as both an input and an output during the execution of a program. since these are passed by reference rather then by value then that are just a pointer as thus resemble the behavior of an alias tag. However it is possible for an InOut parameter value to change during the execution of a program. depending on that ask at hand this behavior could be necessary. InOut parameters can only support one connection, you cannot configure connection to any member of the InOut parameters. An inOut parameter can only be connected to an output parameter if the inout parameter is configured as a constant. InOut parameters are passed by reference which means they are pointing to the base tag, in other words when an inOut parameter is used in logic, the current value of the parameter connected to the InOut parameter is used. Connection to InOut parameters cannot be changed online, unless using the Partial Import online functionality.

InOut tags cannot be used within a subroutine, they only support one connection, can have up to 40 parameters, supports Atomic data types, Structures and Arrays are both supported, online changes to parameters or connections are both supported all for add on instructions. for Programs they can support 512 parameters, support atomic data types, support structures and arrays. but can only support online changes to parameter reference or connection using Partial Import online. 


when we are connecting to a controller, we need to specify what the communication path will be. The syntax for this needs to be the driver name for the selected network/the communications modules' IP address\ the backplane\and the controllers slot number.
Controllers have three modes, run, remote and program. Remote is further divided into three parts, remote run, remote program, and remote test. 

**REMEMBER** download to the PLC, upload to your Host. 

#### Documentation:

So there's a few thins that can be documented in a rockwell project to make it easier for other users to check out what's going on. We  can comment on descriptions in tags, routines, programs, equipment phases, equipment sequences, user-defined types, and add-on instructions. we can also comment on engineering units as well as state identifiers added to tags, user-defined data types or add-on instructions. we can comment on trends, controllers, alarms messages, tasks, property descriptions for modules in the controller organizer. you can also comment on individual rungs, text boxes and FBD boxes. 
- a good way to implement this would be like to add a comment detailing what a routine is doing
- another way is to comment on rungs and explain what the logic contained within a rung is doing


so what if we want to import or export project components. we can export a routine to an 1I5x files, routines in any language can be exported. routines that cannot be exported include any from the add-on instruction container and any softlogix external routines. the export file may also include and program-scoped tags, controller scoped-tags, Add-On instructions, user-defined data types and user defined string types. if they exist within the project the definitions for the referenced tags, the AddOn instructions and user defined types are also exported to a .I5x file
                      
So if you import a routine into a project with routines that have pending edits on other routines, then the edits areaccepted if you slected the Accpet Program Edits when importing. likewise with the finalize all edits in program is selected. However a routine may not be imported into a program if routines that have accepted edits aor test edits.

A routine may not be not be overwritten by a routine of another type. 

what if we want to connect parameters between programs? obviously its really handy to be able to reuse code, so if we wanted to create a program that had parameters to hardware and then we decided to copy that code and changed the parameters we would be able to reuse large amounts of certain code. 

All of the I/O modules in a Logix5000 control system must be owned by a controller, also known as athe owner controller relationship.
- Stores configuration data for every module that it owns.
- Can reside in a location taht differs from the controller.
- sends the I/O module configuration data to define module behavior and begin operation in the control system. 
- Must maintain connection iwth its owner. can only have 1 owner. however other controllers can have listen only connections. you must define the connection type, whenever you download the configs to a controller, then the controller will attempt to establish a connection to them oudels in the config. you can decide how often the controller and module exchange data, using something called the RPI( requested packet interval.) But the module will send its data to the cpntroller either through an IP connection or another communication device and interact withe the owner, and then the owner replicates the process from its side. 
