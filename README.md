#Neural network for house price prediction using tensorflow/Keras
In this project the goals was to train a neural network arquitecture to be able to predict house price. But in this case we do not threat the model as a time-period prediction problem but rather a regression model.

#Dataset
The source of the dataset was the Kaggle House Price Prediction Competition Advanced Dataset.

First I cleaned the data, in this case our data has a lot of missing values and some data is in the wrong format.To handle missing numeric values fill the gaps with the mean of the data in the columns, for other columns I decide to remove some columns , because the number of missing values is greater than 50% of the data, in this case the columns were Alley, PoolQC and MiscFeature

Before move on to train the model I need to scale the data, since we are working we different type of scale in numerical values this could cause some bad performance in the model, so I first testd if my data follow a gaussian distribution, in this case the didn't so I decide to use normalization

#The neural network
For the neural network, I prepare the model using the Keras Sequential object, here below is the complete summary of the model architecture.
Model: "sequential_1"
_________________________________________________________________
 Layer (type)                Output Shape              Param #   
=================================================================
 dense_5 (Dense)             (None, 64)                17664     
                                                                 
 dropout_5 (Dropout)         (None, 64)                0         
                                                                 
 dropout_6 (Dropout)         (None, 64)                0         
                                                                 
 dense_6 (Dense)             (None, 32)                2080      
                                                                 
 dropout_7 (Dropout)         (None, 32)                0         
                                                                 
 dense_7 (Dense)             (None, 16)                528       
                                                                 
 dropout_8 (Dropout)         (None, 16)                0         
                                                                 
 dense_8 (Dense)             (None, 8)                 136       
                                                                 
 dropout_9 (Dropout)         (None, 8)                 0         
                                                                 
 dense_9 (Dense)             (None, 1)                 9         
                                                                 
=================================================================
Total params: 20,417
Trainable params: 20,417
Non-trainable params: 0







