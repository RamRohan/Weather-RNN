# Weather-RNN
This is an RNN model using GPUs to use 24 hours of temperature to predict the temperature for the next 24 hours.

**Dataset**

Dataset contains around 34K values with known labels (for model development), and around 8K values with unknown labels (for scoring).

Dataset included other information, namely temperature, pressure, humidity, location and hour information that could be used to enhance the model.

**Architecture**

I used GPUs to acheive good results for this model. I tried LSTMs, as well as GPU's in combination with LSTMs, and just GPUs gave the best results.

I experimented and tuned with different architectures and layer sizes and the one that gave the best results was 5 GRU layers as an encoder, followed by a dense layer, with the first and the last GRU layer having 1024 units, and the middle three layers having 512 units each.

I tried hyperparameter tuning with l1 and l2 normalization, as well as with batch normalization. These gave good results.

A learnig rate of 0.001125 produced the best results after tuning. 

I ran the trials for 128 epocks with early stopping callback.

The last layer was a dense layer that had the output size of the prediction window which was 24 hours.

**Results**

This achieved an amazing accuracy of 91.85% on the score (unseen) set on submission.
