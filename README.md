# Self_Driving_Car----Semantic-Segmentation
Semantic Segmentation is performed to label the pixels of a road in images using a Fully Convolutional Network (FCN). Kitti Road dataset is used for training the FCN model.
The frozen VGG16 model is hardcoded into helper.py. The model is not vanilla VGG 16, but a fully convolutional version, which already contains the 1x1 convolutions to replace the fully connected layers.
The FCN-8s was trained all at once. The outputs of pooling layers 3 and 4 are scaled before they are fed into the 1x1 convolutions. As a result, the model learns much better with the scaling layers included. The model may not converge substantially faster, but may reach a higher IoU and accuracy.
When adding l2-regularization, setting a regularizer in the arguments of the tf.layers is not enough. Regularization loss terms must be manually added to your loss function. otherwise regularization is not implemented.
