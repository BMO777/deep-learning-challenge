# deep-learning-challenge report:
## Overview of the Analysis
* The purpose of this analysis is to explain the building, training, and results of the multilayered neural network model run with the code provided in the notebook files in the repository

* Data Preprocessing:
  * The `IS_SUCCESSFUL` variable was the target for this model because we are looking to predict how succesful a charity is going to be.
  * The `APPLICATION_TYPE, AFFILIATION, CLASSIFICATION, USE_CASE, ORGANIZATION, STATUS ,INCOME_AMT, SPECIAL_CONSIDERATIONS,& ASK_AMT` variables were the features, and they were dummied into binary form, using pandas_get_dummies function, which makes each row a unique column and files the rows of said column with 0 or 1 depending on the data/classification- similar or idential to OneHotEncoding.
  * In this notebook, the potential features `EIN' and `NAME` were removed, and it seemed one could also remove `SPECIAL_CONSIDERATIONS_Y` or `SPECIAL_CONSIDERATIONS_N`. One or the other, but not both since it seems redundant to leave both.
* Compiling, Training, and Evaluating the Model:
  * 311 Neurons were used in 5 different layers with at least 2 different functions- relu and sigmoid were used for the model here. 
  * The most optimal architecture without causing overfitting of the data is what was sought here, which seemed to be a problem because vaidation accuracy quickly became unchanging- an indication of overfitting. 
  * Also a pyramid neuron distribution shape, with 1st layer having the most neurons and outer layer having the least neurons, was advised and is utilized here.
* Target performance of 75%+:
  * The model here was unable to achive the target performance unfortunately though at least three attempts were made, indicated by three h5 files of saved models. 73% seemed like a limit, though it could be because an early stopping callnack was used to limit epochs based on validation loss plateu with  low patience so the training of the model didnt usually reach the 100 epoch limit set for <p float="left">
  <img src="https://raw.githubusercontent.com/BMO777/deep-learning-challenge/master/model0.png" width="320" />
  <img src="https://raw.githubusercontent.com/BMO777/deep-learning-challenge/master/model1.png" width="320" /> 
  <img src="https://raw.githubusercontent.com/BMO777/deep-learning-challenge/master/model2.png" width="320" />
</p>

* Steps taken in attempt to increase model performance:
  * At 1st a low number of neurons was used but this was quickly increased and seemed to impove the model accuracy to a consistent ~73% accuracy
  * Making sure a upside-down pyramid neuron distribution shape of neurons from most at the initial layer to least at the outer layer seemed to help as well.
  * The best activation function for the initial and hidden layers was relu and for the last or outer layer tahn and sigmoid activation seemed interchangeable.
  * Adding droput layers seemed to increase performance slightly as they are designed to inhibit overfitting.
  * Adding Batch normilization layers between layers except the second last and last layer.
  * Also redusing the learning rate based on loss plateau seemed to help
## Summary:
![](https://raw.githubusercontent.com/BMO777/deep-learning-challenge/master/result1.png)
 * Overall results of the deep learning model: 
  * Best accuracy: ~73% 
  * Best model: Relu/Sigmoid or Tahn for last layer
  * Best # of layers: 6 including last layer
 * Recommendation: RandomForestClassifier, as seen on the last cell of the notebook, said model was used which has the adavantage of less compute time used over the keras sequential model build but seems to have less accuracy- 71.5%- because of less flexibility compared to the keras model.

Code for early stopping based on loss plateau sourced from:https://stackoverflow.com/questions/66530274/tricks-to-improve-cnn-model-performance
