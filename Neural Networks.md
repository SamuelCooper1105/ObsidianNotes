A neural network is a computational model composed of interconnected layers of nodes, lets call these neurons. These networks are designed to recognize patterns and make decisions based on the input.

Okay so lets break this down a bit
1.  **Neurons**: these are the base units of a neural network. Each neuron receives some input, process it, and then passes the output to the next layer. 
	**Layers**: 
		There is the input layer: which receives the initial data 
		Hidden layers: which are intermediate layers that process the data through weighted connections and activation functions
		Output Layer this Produces the final result, like a classification or a prediction
	**Weights and Biases:**
		These are the parameters that the networks learns through the training phase. Weights determine the strength of connections between neurons and biases adjust the output, as needed 
	**Activation Functions**: 
		A function applied to the output of a neuron to introduce non-linearity, this allows the network to learn complex patterns.

2.  **So How does a Neural Network actually work?** 
	- Input Data is passed through the network layer by layer.
	- Each neutron computes a weighted sum of its inputs, adds the biases, and applies the activation function.
	- Final output is generated at the out put layer. 