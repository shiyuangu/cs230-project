# cs230-project
Duplicate_Detection
## Models
* word2vec_v1: simple mean of word vectors.
* word2vec_v2: simple mean of word vectors with manually chosen stop words.
* word3vec_v3: tf-idf weighted mean of word vectors with the same stop words as word2vec_v1
* siamese: siamese network which generalizes tf-idf weighted mean; the weights are learned. 
* siamese+LSTM_v1: compared to siamese, replace the simply summation with LSTM and the weights are fixed to all ones; 
* siamese+LSTM_v2: compared to siamese_v1, the  weights are learned. 
* siamese+LSTM_v3: compared to siamese_v2, use l2-regulization instead of early stopping for weights. Performance became worse.
* siamese+LSTM_v1+LSTM: add another LSTM layer on top of  siamese+LSTM_v1. 
* siamese+LSTM_v2+LSTM: add another LSTM layer on top of  siamese+LSTM_v2.
* siamese+biLSTM+LSTM: compared with siamese+LSTM_v2+LSTM, replaced the first LSTM with bi-LSTM. 

## Performance Tunning 

For siamese+LSTM, time is  for training 1 epoch (323232 training examples), GPU-Util is from nvidia-smi. This timing result is for model.fit(), and model.predict(x, batch_size) is also sensitive to the batch_size.  

batch_size = 32(default): CPU: ~600s

Amazon-EC2-P3.2xlarge, Tesla V100-SXM2-16GB, 

Deep Learning AMI (Ubuntu) Version 19.0 (ami-00fc7481b84be120b)


batch_size | Time | GPU_Util 
------------ | ------------- | ----------
32(default) | ~10m | 30% 
128| ~300s | 
256| 160s | 
1024 | 46s |
2048 | 24s | 70%
4096 | 14s | 86%
8192 | 8s (**best**) | 90%+
16284 | 7s | 90% 
32568 | 32s | 100% (slow starting) 
