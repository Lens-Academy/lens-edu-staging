---
id: 99cf038c-e705-43b5-92ac-00a7be727bd9
title: "But what is a Neural Network?"
summary_for_tutor: "Grant Sanderson's 3Blue1Brown lesson (text adaptation by Josh Pullen) explains the structure of a plain neural network using handwritten digit recognition. The example network has 784 input neurons (28x28 pixels), two hidden layers of 16 neurons each, and 10 output neurons. Each neuron's activation is a sigmoid of the weighted sum of the previous layer's activations plus a bias. The hope is that successive layers detect edges, then loops and lines, then digits. The network has 13,002 weights and biases, can be written compactly as matrix multiplication, and is ultimately just a function from 784 numbers to 10. A bonus note explains why ReLU has replaced sigmoid. How the network learns (gradient descent) is left to the next lesson, which the lens links."
---

#### Embed
source:: [[../articles/sanderson-but-what-is-a-neural-network]]

#### Text
content::
This is the first lesson in 3Blue1Brown's neural networks series. If you want to go deeper, the next lesson on gradient descent and how networks learn continues it: https://www.3blue1brown.com/lessons/gradient-descent
