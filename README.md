# qmnist_typ_class_nn

Some work for this project was directly used in the McGill course ECSE 551, and the professor has requested that I not post the code related to this project. 

Refer to my website for a quick description of the objectives and results - https://davwyr.com/portfolio/Projects/ML_projects....

What is posted here is primarily a perusal of a few different models that were not explored (and some that were explored) in the ECSE 551 project.
This repo and the results therein are mainly to demonstrate my ability to tamper with different models on a given classification task. 

This classification was on 28x28 pixel greyscale images. The only real pre-processing step was a "normalization" of sorts, to bring the pixel values from the range
[0, 1] to the range [-1, 1]. The project was primarily done using the PyTorch library. Some zero-padding was used in pre-processing for the LeNet-5 model as well.

Refer to the .csv file in this repository for a fully tabulated view of the results. I'll explain the features of the particular models below:

1. Regular:

  - This is an ordinary feed-forward fully-connected neural net with 3 hidden layers: 784 (28x28) -> 256 -> 128 -> 64 -> 10 (number of classes)
  - Activation Function: ReLU
  - Loss Function: Cross-Entropy Loss
  - learning rate = 6e-2
  - SGD optimizer, momentum = 0.9
  - number of training Epochs: 2000

2. Conv1:

  - Activation Function: Leaky ReLU - negative slope = 0.01
  - Loss Function: Cross-Entropy Loss
  - learning rate = 0.001
  - ADAM optimizer
  - number of training Epochs: 100

  Consists of convolutional layers followed by fully-connected layers.
  
  Convolutional Layers:
       (kernel=5x5, stride=1)      (maxPool-2d, stride = 2)     (kernel=3x3, stride=1)      (maxPool-2d, stride = 2)     (kernel=2x2, stride=1)
  28x28x1        ->       24x24x10          ->           12x12x10          ->        10x10x32          ->          5x5x32           ->        4x4x64
  
  Fully-Connected Layers:
  
  4x4x64=1024    ->    500   ->    100    ->    10

3. Conv2:

  - Activation Function: Leaky ReLU - negative slope = 0.01
  - Loss Function: Cross-Entropy Loss
  - learning rate = 0.001
  - ADAM optimizer
  - number of training Epochs: 100

  Consists of convolutional layers followed by fully-connected layers.
  
  Convolutional Layers:
       (kernel=5x5, stride=1)      (maxPool-2d, stride = 2)     (kernel=3x3, stride=1)      (maxPool-2d, stride = 2)     (kernel=3x3, stride=1)
  28x28x1        ->       24x24x5          ->           12x12x5          ->        10x10x10          ->          5x5x10           ->        3x3x20
  
  Fully-Connected Layers:
  
  3x3x20=180    ->    100   ->    50    ->    10

4. Conv3:

  - Activation Function: Leaky ReLU - negative slope = 0.01
  - Loss Function: Cross-Entropy Loss
  - learning rate = 0.001
  - ADAM optimizer
  - number of training Epochs: 100

  Consists of convolutional layers followed by fully-connected layers.
  
  Convolutional Layers:
       (kernel=5x5, stride=1)      (maxPool-2d, stride = 2)     (kernel=5x5, stride=1)      (kernel=3x3, stride=1)     (kernel=3x3, stride=1)
  28x28x1        ->       24x24x12          ->           12x12x12          ->        8x8x24          ->          6x6x48           ->        4x4x60
  
  Fully-Connected Layers:
  
  4x4x60=960    ->    100   ->    40    ->    10

5. LeNet-5 architecture:

Here, we added two layers of zero-padding to increase the input size of the images accordingly

  - Activation Function: Leaky ReLU - negative slope = 0.01
  - Loss Function: Cross-Entropy Loss
  - learning rate = 0.001
  - ADAM optimizer
  - number of training Epochs: 100

  Consists of convolutional layers followed by fully-connected layers.
  
  Convolutional Layers:
     (kernel=5x5, stride=1)      (AvgPool-2d, stride = 2)     (kernel=3x3, stride=1)       (AvgPool-2d, stride = 2)     
  28x28x1        ->       24x24x6          ->           12x12x6          ->        10x10x16          ->          5x5x16
  
  Fully-Connected Layers:
  
  5x5x16=400    ->    120   ->    84    ->    10

6. Conv1_dropout:

  Same model as Conv1, but added dropout=0.5 after select convolutional and fully-connected layers.

  
7. Conv2_dropout:

  Same model as Conv1, but added dropout=0.5 after select convolutional and fully-connected layers.

8. Conv3_dropout:

  Same model as Conv1, but added dropout=0.5 after select convolutional and fully-connected layers.

9. LeNet-5_dropout:

  Same model as Conv1, but added dropout=0.5 after select convolutional and fully-connected layers.
