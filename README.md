# cs230-project
Duplicate_Detection
## Performance Tunning 

For siamese+LSTM, time is  for training 1 epoch (323232 training examples), GPU-Util is from nvidia-smi: 

batch_size = 32(default): CPU: ~600s


batch_size = 32 (default) : ~10m, GPU_util: 30%

btach_size = 128: ~300s, 

batch_size = 256: 164s 

batch_size = 1024: 46s 

batch_size = 2048: 24s, GPU_util: 70%

batch_size = 4096: 14s, GPU_util: 86%

batch_size = 8192: 8s, GPU_util: 90%+ (*Best*)

batch_size = 16284: 7s, GPU_util: 90% + 

batch_size = 32568, 32s, GPU_util: ~100% (beginning is slow)  
