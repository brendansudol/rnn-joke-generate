
This code uses a multi-layer Recurrent Neural Network (RNN) character-level language model open-sourced by [Andrej Karpathy](https://github.com/karpathy/char-rnn) (described in detail [here](http://karpathy.github.io/2015/05/21/rnn-effectiveness/)) to generate late-night comedy monologue jokes.

The dataset is the concatenation of Conan O'Brien monologue jokes over the last ~5 years (1.3MB). I used a 2-layer LSTM with 512 hidden nodes and a dropout of 0.25, 0.5, and 0.75, and ran it on an Amazon EC2 instance with GPU (see [here](http://blog.titocosta.com/post/110345699197/public-ec2-ami-with-torch-and-caffe-deep-learning)) to speed up the training (~15x faster than CPU).

**train**

```bash
th train.lua -data_dir data/conan -rnn_size 512 -num_layers 2 -dropout 0.5
```

**sample**

```bash
th sample.lua cv/cpu/d50_1.1565.t7_cpu.t7 -temperature 1 -length 10000
```
