# 1.  Image normalization

This is a process to change the pixel intensity values in the input image. For example if we are using a grey scale image, then the pixel intensity values range from 0 to 255.



## 2. 3x3 convolutions

It has been observed that 3x3 kernel is the best filter that can be used for convolution. 3x3 kernel, when used reduces the resolution by 2, for example an image having a resolution of 400x400, the next layer becomes 398x398.


## 3. How many layers?

This is based on the image size and in our scenario; we have assumed that the size of the image is equal to the size of the image. Suppose if am taking a image of size 400x400 and if I want to reach 1x1 using 3x3 kernels (with no consideration of other concepts like 1x1, maxpooling etc.) then we need to add 400/2 = 200 convolution layers need to be added.


## 4. Kernels and how do we decide the number of kernels?

Kernels are feature extractors from an image, for example to extract vertical edges, horizontal edges out of an image.
The number of are decided depending on the several factors such as the number of features each kernel has to extract i.e. more number of unique features to be extracted, then more kernels. 


## 5. Receptive Field

We consider this as Global receptive field, which helps us to tell us the information of where I started and where I am in my convolution network. For example if I convolved an image of resolution of 49x49 to 25x25 using 3x3 kernels, then my global receptive field is 24x24


## 6. Max Pooling

We have seen that by adding only 3x3 kernels for convolutions, the number of layers increase if the image size if big. Max pooling is used to reduce the number of layers and reduces the image size to half. Global receptive field, however doubles when max pooling is applied. 


## 7. Position of MaxPooling

Maxpooling is desired after convolution layers and it’s positioned after every 2 to 3 convolution layers. Also, it’s always better to avoid using the same before last 2 -3 layers, where final convolved image is obtained.


## 8. 1x1 convolutions

This is used generally to reduce the number of channels. This is usually done after some convolution layers, where all the pixel values of each channel is merged with pixels values of the other and an output is obtained for each pixel i.e. it merges the pixel values and provides a scaled output thus keeping the resolution of the image same. 


## 9. Concept of Transition layers

Transition layer is a combination of 1x1 and Maxpooling and is generally applied post some convolution layers. There is no clear evidence as to use 1x1 first or max pooling first but preferably, we use 1x1 first and then Maxpooling


## 10. Position of Transition Layer
This is always preferred post 2-3 layers of convolution and avoided at the last 2-3 layers.


## 11. The distance of MaxPooling from Prediction

Maxpooling should be at least 2-3 layers before the prediction layer. For example, an image (3) is convolved, if maxpooling is applied at the end layer, all that remains in the image will be a representation of dot.


## 12. Batch Normalization

This is used to decide the output of each batch i.e. finalize the outputs by normalizing the values from -1 to 1. This ensures that Kernels has learnt with some definite output at the end of each batch


## 13. The distance of Batch Normalization from Prediction

It’s better to avoid batch normalization in the last layer since it normalizes the values from -1 to 1 and we don’t have any information being lost out in the last layer


## 14. Softmax

Softmax ensures that network gives a decisive and a better accuracy, when applied at the last layer. This is better when compared to the results without applying the softmax. Having said that, this is not a complete probability but its probability like.


## 15. DropOut

Dropout negates and deactivates few pixels before the next convolution or transition layer is invoked. This ensures other kernels learn more to compensate this loss of information. 

## 16. When do we introduce DropOut, or when do we know we have some overfitting

When the training accuracy of the model is increasing, i.e. the data is mugged up for each iteration and validation accuracy does not perform well, in this case there is overfitting of the model. Droput is used to prevent overfitting and it increases the validation accuracy.


## 17. When to add validation checks

Validation check should be applied for each epoch to keep track on our validation accuracies. This helps us to conclude whether our network is performing well or not

## 18. How do we know our network is not going well, comparatively, very early 

When the validation checks are applied for each epoch, the validation accuracies observed on the first few epochs, helps us to conclude whether the network is doing good or bad

## 19. Batch Size, and effects of batch size

Batch size - Number of images in the dataset chosen for training. For example of batch size of 32, means 32 forward propagation and one backward propagation are performed. 
Batch size increases the validation accuracy slowly but after some point, the accuracy starts dropping slowly. It always ideal to have a batch having the data belonging to all classes (possibly)

## 20. Number of Epochs and when to increase them

Epoch is the complete training iteration of all the items in the dataset once. When the validation accuracy is getting better, we can add more epochs to if it continues to improve and desired result is obtained.

## 21. Learning Rate

When the validation accuracy of a model reaches a saturation point and neither increases nor decreases, then learning rate is applied to the model. 

## 22. LR schedule and concept behind it

It schedules the learning rate based on the number of epochs. Training or validation accuracy does not affect the learning rate and it predefines the learning rate for each epoch

## 23. Adam vs SGD

Adam is an optimization algorithm to update network weights iteratively whereas SGD only computes on a small subset or random selection of data examples.


## 24. When do we stop convolutions and go ahead with a larger kernel or some other alternative (which we have not yet covered)

Taking the example of convolving an image having a representation of number 3, after several convolutions, the whole image is achieved in let’s say 7x7 resolutions. Now at this point, if we continue applying 3x3 kernels and convolve, the image 3 will be reduced to the representation of a dot. In other terms when we are able to extract all features of the image at 7x7, then it is better to apply a 7x7 kernel instead of 3x3 kernel, to get the final output






