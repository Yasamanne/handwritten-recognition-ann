# handwritten-recognition-ann
 build an ANN model to recognize handwritten digits

The Neural network model is developed using the keras package in Python.
The steps include:

1. Load data from mnist dataset from keras sample datasets

   
2. Split data to train and test (12665 train records & 2115 test records)

   
3. Filter by index for taking only 2 classes (0 and 1)

4. Scale images to range[0,1] (normalization) --- which improves accuracy at the same time keeps the importance of each variable

5. Covert class vectors to categorical class matrices to avoid giving any importance to
output classes

6. Creating a model with the help of keras.Sequential() which groups a linear stack of
layers

7. Then add 1 input layer in which the data shape is 28X28 but needs to be flattened since because the input layer should only be a 1-dimensional array we would have 784 nodes in the first layer

8. Then create a hidden layer with layers.Dense(14, activation='relu') ranges of 2 to 20 nodes for this layer have been checked and all of them share the same results of over 99 percent accuracy but with more nodes more time to process is required, and the
activation function used is ‘relu’ to give non-linearity to the model and it's a very popular because it doesn’t active all the neurons at once so the nodes are 14 in this layer

9. After that, the output layer with layers.Dense(2, activation=’sigmoid’) is added 2 is the number of classes and sigmoid is selected because of its binary classification but we could have also applied softmax which is usually used for multi-class classification but can be applied for binary as well. So the nodes are 2 in this layer


10. Then we compile the model and use the model. compile() we pass some parameters like :
loss='categorical_crossentropy. We use loss as categorical cross entropy because the
classes are one-hot-encoded


11. Then set optimizer= keras.optimizers.Adam(learning_rate= 0.01), metrics=['acc'] and
Adam was selected as optimizer since the Adam optimizer produces better results than
other optimization methods, has a shorter calculation time, and requires fewer tuning
parameters. As a result of all of this, Adam is suggested as the default optimizer for the majority of applications. The metric is accuracy because FP and FN have no difference for us to use recall and precision. Accuracy = (TP+TN)/(TP+FP+TN+FN)

12. The criteria for early stopping have been added keras.callbacks.EarlyStopping and its based on loss value the patience is set to 9 because the normal rate of saturation is between 8-10

13. Epochs are set to 100 which normal is for a column size of 28 and that’s the number of times weights are changed going forward and backward

14. A batch size of 32 or 25 is good with 100 epochs which is the number of inputs in get process at a time

15. The confusion matrix shows TP, FP in the first row and FN, TN in the second row

16. For using different initializers 3 types of initializers were selected and it didn’t change the accuracy all of the models have an accuracy above 99percent the seed was kept the same for all of the initializer generators

17. kernel_initializer_1 = keras.initializers.RandomNormal(mean=0., stddev=1., seed=seed)

18. kernel_initializer_2 = keras.initializers.TruncatedNormal(mean=0.0, stddev=0.05,
seed=seed)


19. kernel_initializer_3 = keras.initializers.RandomUniform(minval=-0.05, maxval=0.05,
seed=seed)
