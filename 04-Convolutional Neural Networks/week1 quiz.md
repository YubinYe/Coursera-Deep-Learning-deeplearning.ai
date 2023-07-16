## Week 1 quiz - The basics of ConvNets



1. What do you think applying this filter to a grayscale image will do?
![image](https://github.com/YubinYe/Coursera-Deep-Learning-deeplearning.ai/assets/25284440/94293216-873b-47e2-9f60-8a40f090db1e)

  - Detect horizontal edges

  - Detect vertical edges

  - > Detect 45 degree edges

  - Detect image contrast

2. Suppose your input is a 300 by 300 color (RGB) image, and you are not using a convolutional network. If the first hidden layer has 100 neurons, each one fully connected to the input, how many parameters does this hidden layer have (including the bias parameters)?

  - 9,000,001

  - 9,000,100

  - 27,000,001

  - > 27,000,100
    
  > (300 * 300 input pixel * 3 colors + 1 bias ) * 100 neurons

  > Suppose your input is a 128 by 128 color (RGB) image, and you are not using a convolutional network. If the first hidden layer has 64 neurons, each one fully connected to the input, then parameters of hidden layer:
  ->  (128 * 128 input pixel * 3 colors + 1 bias ) * 64 neurons 

3. Suppose your input is a 300 by 300 color (RGB) image, and you use a convolutional layer with 100 filters that are each 5x5. How many parameters does this hidden layer have (including the bias parameters)?

  - 2501

  - 2600

  - 7500

  - > 7600
    
  > (5 * 5 filter pixel * 3 colors + 1 bias ) * 100 filters

  > Suppose input is a 256 by 256 color (RGB) image, and a convolutional layer with 128 filters that are each 7x7.
  -> parameters of hidden layer: (7 * 7 filter pixel * 3 colors + 1 bias ) * 128 filters

4. You have an input volume that is 63x63x16, and convolve it with 32 filters that are each 7x7, using a stride of 2 and no padding. What is the output volume?

  - 16x16x32

  - 29x29x16

  - > 29x29x32

  - 16x16x16
    
  > (63 input pixel + 2 * 0 padding - 7 filter pixel )/stride 2 + 1 bias = 29
  -> 29 * 29 * 32 filters

5. You have an input volume that is 15x15x8, and pad it using “pad=2.” What is the dimension of the resulting volume (after padding)?

  - 19x19x12

  - 17x17x10

  - > 19x19x8

  - 17x17x8
  
  > padding is applied over the height and the width of the input image. If the padding is 2, you add 4 to the height dimension and 4 to the width dimension.

6. You have an input volume that is 63x63x16, and convolve it with 32 filters that are each 7x7, and stride of 1. You want to use a “same” convolution. What is the padding?

  - 1

  - 2

  - > 3

  - 7
  
  > when using a padding of 3 the output volume has n_H = (63 + 2 * 3 padding - 7 filter pixel )/1 stride + 1 bias

  > if the input volume that is 63x63x16, with 40 filters that are each 9x9, and stride of 1. if padding = 4, then
  ->  n_H = (64 + 2 * 4 padding - 9 filter pixel )/1 stride + 1 bias = 64

7. You have an input volume that is 32x32x16, and apply max pooling with a stride of 2 and a filter size of 2. What is the output volume?

 - 15x15x16

  -> 16x16x16

  - 32x32x8

  - 16x16x8
    
  >  n^{l}_H = (n^{l-1}_H + 2p - f)/s + 1
  -> n_H = (32 + 2 * 0 padding - 0 filter pixel )/2 stride + 0 bias = 16

8. Because pooling layers do not have parameters, they do not affect the backpropagation (derivatives) calculation.

  - True

  - > False

> the hyperparameters for a pooling layer are:
-> Filter size, Stride, Max or average pooling
  
  
9. In lecture we talked about “parameter sharing” as a benefit of using convolutional networks. Which of the following statements about parameter sharing in ConvNets are true? (Check all that apply.)

  - It allows parameters learned for one task to be shared even for a different task (transfer learning).

  - >  It reduces the total number of parameters, thus reducing overfitting.

  - It allows gradient descent to set many of the parameters to zero, thus making the connections sparse.

  - > It allows a feature detector to be used in multiple locations throughout the whole input image/input volume.
    
> The benefits of using convolutional layer:
-> it reduces the total number of parameters, thus reducing overfiting parameter sharing.
-> convolutional layers are good at capturing translation invariance

10. In lecture we talked about “sparsity of connections” as a benefit of using convolutional layers. What does this mean?

  - Each filter is connected to every channel in the previous layer.
  - > Each activation in the next layer depends on only a small number of activations from the previous layer.

> the following images depicts the result of a convolution at the right when using a stride of 1, and the filter is shown right next.![image](https://github.com/YubinYe/Coursera-Deep-Learning-deeplearning.ai/assets/25284440/c34cde41-79ea-4e99-92f3-a7a2ad091465)

    - > it depends on the pixels enclosed by the green square.
