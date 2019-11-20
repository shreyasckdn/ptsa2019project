# ptsa2019project
Project about Residual Recurrent Neural Networks


### Shreyas - 11/14/2019

Progress so far

Read through the paper fully

Got climate data (ENSO: 2 datasets Nino 3.4 and Nino1.2) that is used in the paper. Got it formatted right as well

Tried fitting ARIMA model as in the paper. Model fit very well. much better than the paper. Not sure
where i am going wrong here. paper is also not clear at a few places

paper does not mention
1. if results are on test or val for ENSO
2. which lag they finally used
3. if/how they used regularization in arima
4. mean is subtracted from training data. but how to rescale predictions? adding
means to predicted data is giving near perfect results

insights for both datasets are same

Tried RNN model using LSTM. Able to train a model and see some result. but lots of debugging still left
used code from https://towardsdatascience.com/lstm-for-time-series-prediction-de8aeb26f2ca#:~:targetText=The%20idea%20of%20using%20a,looking%20only%20at%20its%20past.

### Shreyas - 11/20/2019

### meeting 1:

the data given is mean data
anomaly might correspond to SD or max values in a month

### feedback from cristina:

she was not sure what 'In the case of the ENSO dataset, we perform a 6 month ahead prediction, which means that the minimum
possible lag of VAR was 6' means
suggested to first try on fake data
1. create fake ar(1) and model it using ar(1) to check if ar(1) works
2. add non linearity and model it using ar(1)
3. try to improve the fit using lstms and r2n2

six month ahead prediction does not mean that the x_t should depend on x_{t-6} or later
we can fit any ar(p) model and perform six month ahead prediction

### changes made to code:

fixed data being used (only mean data)
subtracting the means for each month across all years in training before feeding data to model
rescaling prediction data is just adding the calculated training means
not using anomaly data for now

created fake ar(1) data, modeled it and analyzed residuals. model works as expected
added non linearity and modeled it

to do:
run lstm on fake non linear data
run r2n2 on fake non linear data
