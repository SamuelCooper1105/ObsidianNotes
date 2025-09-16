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

#### Hardware Tags

hardware tags are automatically created by rockwell software when you add hardware. These are module defined data types that are related to a specfic module. we should be able to connect hardware tags to parameters so that the program can connect to the hardware and modify the external values of that hardware. The data types in the tags and the parameters must be the same. 
