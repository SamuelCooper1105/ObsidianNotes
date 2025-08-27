React uses components, which are elements of the UI, to create applications. Components can either be a function or a class. Function components return markup, and Class Components extend React.Component. 

Props or properties are read only inputs to components, this allows for data in function to be passed from a parent to a child. 
State is a data type that changes over time, usually in response to user actions. State is managed within a component and can be updated using the useState hook in function components. 

The useState function is unmutable, as in we do not change the actual data itself ever. The use state returns two objects, a value that we use to measure state and a function to change the state. for example `` const [IsTrue, setIsTrue] = useState(true);`` this code returns the value of the state we are checking IsTrue which will be a Boolean value as defined by the type set by the useState declaration. setIsTrue is the function to change the value IsTrue. Typically we don't want to explicitly change the data, but exceptions are made like in this example. where we use the setIsTrue function to explicitly change IsTrue from true to false, like so ``setIsTrue=(!IsTrue)``.  

