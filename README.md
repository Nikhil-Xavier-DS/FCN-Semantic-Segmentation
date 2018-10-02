# Self_Driving_Car----Semantic-Segmentation

Semantic Segmentation is performed to label the pixels of a road in images using a Fully Convolutional Network (FCN). Kitti Road dataset is used for training the FCN model. Useful information about the model is given below.

1. The frozen VGG16 model is hardcoded into helper.py. The model is not vanilla VGG 16, but a fully convolutional version, which already contains the 1x1 convolutions to replace the fully connected layers.
2. The FCN-8s was trained all at once. The outputs of pooling layers 3 and 4 are scaled before they are fed into the 1x1 convolutions. As a result, the model learns much better with the scaling layers included. The model may not converge substantially faster, but may reach a higher IoU and accuracy.
3. When adding l2-regularization, setting a regularizer in the arguments of the tf.layers is not enough. Regularization loss terms must be manually added to your loss function. otherwise regularization is not implemented.

Model Design:

1. Classical VGG-16 model is modified into FCN (Fully Convoluted Network) by replacing fully connected layers with 1x1 convolution layer. Skip connections are used along with adding 1x1 convolutions on other earlier VGG layers and transposed convolution. The transpose convolution layer will have kernel initializer along with regularizer.
2. Cross-entropy is used as loss function.
3. Adam optimizer is used as optimizer.

Hyperparameters:

1. Keep probability (drop out rate) = 0.5
2. Learning rate = 0.001
3. Batch size = 5
4. Number of epochs = 25
