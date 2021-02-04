# trading_assistant

Although there is a lot of noise and random walks in prices of any type of security, I want to see if a recurrent neural network can learn to predict price movements to some extent. I configured [this model](https://github.com/emrealtinok/trading_assistant/blob/main/TradingAssistant.ipynb) to predict the direction of the price on the next time step at any given time, so basically it's not a trading bot. The network merely suggests a short-term momentum. I also compared the accuracy of the model to the accuracy of three different ensemble classifiers from scikit-learn [here](https://github.com/emrealtinok/trading_assistant/blob/main/TradingAssistant(sklearn).ipynb).

I imported data from [this website](https://eaforexacademy.com/software/forex-historical-data/) to train my model. It provides csv files that contain 200,000 bars of currency prices.  

I coded in most of the popular technical indicators that traders use to analyze price movements, like RSI, MACD, Bollinger Bands etc. I used these to genarate training data for my model. I picked typical price, which is the average of the close, high and low prices, for my predictions instead of the close price, as I think typical price is a better indicator of the price of a bar. 

I set up a recurrent network with two LSTM layers and a Dense layer, followed by the final layer with a sigmoid activation function. I used binary crossentropy to calculate the loss.  

Honestly, I thought that the accuracy of the model would stay close to 50% due to all the randomness and the even distribution of ups and downs in the actual output set. I was suprised to see it go up to 62-63% accuracy. This made me think that this model can be used as a short-term momentum indicator.

The recurrent neural network outperformed the ensemble classifiers from scikit-learn by 2-3%.

I will keep on working on this model and test out more of the common startegies that these technical indicators are used for.
