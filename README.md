# Neural network for house price prediction using tensorflow/Keras

The gaol of this project is to build a deep neural network arquitecture to make house price prediction base on diferent features that houses present, the approach of to make this prediction is as a regression problem, we knwo that house prices variate widely over time, but in this case our dataset is just base on attributes of the houses and his sales prices rather than price of the house over time, so in this case this project is not about forecasting prices but to predict the possible price of a house base on their attributes.

 # Dataset

The source of the dataset was the Kaggle House Price Prediction Competition Advanced Dataset.

First I cleaned the data, in this case our data has a lot of missing values and some data is in the wrong format.To handle missing numeric values fill the gaps with the mean of the data in the columns, for other columns I decide to remove some columns , because the number of missing values is greater than 50% of the data, in this case the columns were Alley, PoolQC and MiscFeature

Before move on to train the model I need to scale the data, since we are working we different type of scale in numerical values this could cause some bad performance in the model, so I first testd if my data follow a gaussian distribution, in this case the didn't so I decide to use normalization

# The neural network

For the neural network, I prepare the model using the Keras Sequential object, here below is the complete summary of the model architecture.
```
def build_model():
    model = Sequential()
    model.add(Dense(64,kernel_initializer='normal', input_dim=275, activation='relu'))
    model.add(Dropout(0.2))
    model.add(Dropout(0.2))
    model.add(Dense(32,activation='relu'))
    model.add(Dropout(0.2))
    model.add(Dense(16,activation='relu'))
    model.add(Dropout(0.2))
    model.add(Dense(8,activation='relu'))
    model.add(Dropout(0.2))
    model.add(Dense(1,activation = 'linear'))
    model.compile(loss='mean_squared_error', optimizer=optimizer, metrics=['mse', 'mae'])
    return model
```
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

# Trainnig the model and evaluate performances

We now start to fitting the model adn start the training phase with 500 epochs and batch_size, afert the training we evaluate the mean saure erroa dn plotting to see the results

![image](https://user-images.githubusercontent.com/86735728/182750870-2d72287b-532c-4615-a28e-6645791fbb8d.png)

Base on this image above we saw that model is leanring well but not as good as it's should, base on the analysis of the errorwe conclude that the model is unnstable, this could be solve by tunnig hyperparameters like the epochs or using regularization and changing the learning, rate, we found that learning rate less than 0.03 could cause innestability on the learning. 

# Making some predictions 
after the optimization we perform prediction tests with a test dataset, this are the results 

array([[149190.06],
       [158010.23],
       [158180.06],
       [176980.47],
       [149111.11],
       [229571.56],
       [148512.72],
       [132880.73],
       [150227.83],
       [201350.75],
       [149336.38],
       [129995.53],
       [201350.75],
       [122241.75],
       [180679.2 ],])
As you can see in this array, this are the prices predicted by the model, and here is a much condese overview of all the predictions maded.
![image](https://user-images.githubusercontent.com/86735728/182751763-4128d93d-0ba8-4933-9d79-663e627833df.png)






