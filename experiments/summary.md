# Experiments on CVM model

In order to determine the best configuration parameters for the model and the training session, we decided to conduct various sessions of training-evaluation on the model while changing one parameter at the time. We can group those parameters into two :
-   **Architecture parameters** : these parameters are directly linked to the model. They are mostly convolution parameters such as *filters sizes, channels, dilation, number of convolution layers*.
-   **Training parameters** : they are represented by the _number of epochs, the loss function, the slicing of the dataset_.

### Architecture parameters

### Training parameters
Regarding the training parameters, we fixed number of epochs to _150_ and sliced the dataset into fixed-length sequences of _81 frames_ for equity. Only the _loss fonction_ was modified. There are three functions that we decided to use during:
*   Position Loss :
*   Motion Loss :
*   Laplacian Loss :