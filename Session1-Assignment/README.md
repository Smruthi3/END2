## This is Readme for 1st session assignment

1. What is a neural network neuron?

Ans : Neuron in a neural network is small memory or a signal which keeps the compuation unit outside of it


2. What is the use of the learning rate?

Ans : Learning rate helps to get a optimal weights and these weights intern minimizes the training loss

	 The only caveat here is optimal value of the learning rate has to be chosen to swifty reach the global minimum point, 
	 if learning rate value is too low or too high requires many updates or leads to divergent behavior respectively

3. How are weights initialized?

Ans: In the following ways weights in the neural network can be initialized:

	* weights are initilized with zero values. This way of initialization causes the neuron to memorize the the same functions 
	  almost in each iterations and prevents the model to learn new features becasue of which model gets stcuk.
	* To overcome the previous issue, weights are initilized with small random weights. 
	  Though this is a better choice,initializing weights with much high or low random value can result in  divergence or slower optimization respectively
	* Recommended way is to initilize the weights with randomly from a normal distribution where mean of the activation function is zero and variance of the activations should stay the same across every layer (xavier initialization)


4. What is "loss" in a neural network?

Ans: Loss in a neural network corresponds to differnce between predicted output and actual output


5. What is the "chain rule" in gradient flow?

Ans: Gradient flow is the set of rules used by Backpropagation algorithms to compute gradients and chain rule is used to calculate the final gradient value which is later used to calclate the new weights
 
	 Basically to obtain a (∂Error / ∂oldweight) chain rule is used and it can be described as follows

	 Final gradient = Gradientcontribution1 + Gradientcontribution2

	 Gradient1=GradientInside×GradientContribution1 

	 or

	 ∂Output/∂wi = ∂Contribution1 / ∂wi * ∂Output / ∂Contribution1   
