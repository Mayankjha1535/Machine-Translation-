# Machine-Translation

In this project, I have implemented three different models to translate from english to german. The main framework is encoder-decoder approach. Encoder encode the given sentence and converts the source sentence in a fixed length context vector. The hidden state of the decoder is initialised with the fixed length context vector. The deccoder predicts the target sequence. 

Preprocess.ipynb contains the code for basic preprocessing

Three different models used are :-

# Unconditional Encoder - Decoder 
This model just uses the last hidden state of the encoder and based on that the decoder generate random words. Hence, it performed the worst.

# Conditional Encoder - Decoder

In this model, the decoder is initialised with the last hidden state of the encoder. At any timestep, the decoder along with the previous timestep takes the previous predicted word as input. Thus, the model becomes conditional on the previous predicted words. This model performed much better than the unconditional encoder decoder model.

# Attention model

As the previous models were failing for the translation of long sentences. Hence, in this model, I implemented additive attention. The main idea behind attention is that at any timestep the decoder should focus on the relevant words in the encoder. To calculate attention, the output of encoder at each and every timestep were taken into account along with the words predicted till now by the decoder. This model outperformed all the earlier models.

# Plot Attention weights

I also investigated the role of attention by plotting attention weights. This shows the focus of the decoder on the specific words of the encoder at each timestep.

# Model evaluation

I evaluated the model using BLEU score.
Attention model achieved the highest 0.29 BLEU-4 score.
|MODELS|BLEU-1|BLEU-2|BLEU-3|BLEU-4|
|------|------|------|------|------|
|Unconditional Encoder-Decoder|0.44|0.30|0.23|0.13
