# Image Coloring Using Autoencoders


### Problem Statement

To color a black and white image.


### Dataset

The dataset used can be found here: https://www.kaggle.com/kmader/food41


### Model



##### Model Config:

input_shape = (256, 256, 1)
batch_size = 64
kernel_size = 3
latent_dim =  512
Optimizer : Adam
Loss: MSE

An Autoencoder model has been used for this purpose.


##### Encoder
1. The Encoder has an Input Layer accepting tensor of shape  (256, 256, 1).
2. It has 32, 32, 64, 64,128 filers in "Conv2D" layers, all having "relu" as activation function, and "stride" of 2.
3. Then a "Flatten" layer has been used to flatten the vectors.
4. The vectors are then fed to a "Dense" layer having a size of "512" which is the representation of the image in the latent dimension.





##### Decoder

1. The decoder has an "Input" layer accepting tensor of shape 512.
2. Next, it has a "Dense" layer having a size of the ( filters*image_height*image_width ) from the last "Conv2D" layer in Encoder.
3. A "Reshape" Layer reshapes the tensors in the shape of (image_height, image_width, filters).
4. Next, it is fed to "Conv2DTranspose" layers having   128, 64, 64, 32, 32, filers ", all having "relu" as activation function, and "stride" of 2.
5. Next, The tensors are fed to a last "Conv2DTranspose" layer having 3 filters. Which is the output.




##### Callbacks During Training

1. Learning Rate Scheduler has been used to reduce the learning rate if the model stops improving for the next 3 iterations.
2. Early Stopping has been used that monitors "validation loss" if the model doesn't improve for the next 5 iterations.


##### Encoder
<img src="https://github.com/mahesh863/Image-Coloring-Autoencoders/blob/main/images/encoder.png" height=500px>




##### Decoder
<img src="https://github.com/mahesh863/Image-Coloring-Autoencoders/blob/main/images/decoder.png" height=500px>




### Training

The model was initially planned to train for 50 epochs. But the model's validation loss was not improving much so the training was stopped after 24 iterations to prevent overfitting.


##### Loss Graph

<img src="https://github.com/mahesh863/Image-Coloring-Autoencoders/blob/main/graph/losss.png" width="500px" >

 



### Results

The results could be way better if the model was trained with more data and more fine tunning would be done.

##### Input

<img  src= "https://github.com/mahesh863/Image-Coloring-Autoencoders/blob/main/images/input.png" width="500px" >




##### Model Output

<img  src= "https://github.com/mahesh863/Image-Coloring-Autoencoders/blob/main/images/pred.png" width="500px" >


##### Acutal Output

<img  src= "https://github.com/mahesh863/Image-Coloring-Autoencoders/blob/main/images/true.png" width="500px" >




### Conclusion


More of hyperparameter optimization can be done to improve the. I will be doing it in the future.
