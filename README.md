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
![2](https://user-images.githubusercontent.com/28965732/97304309-91268280-1881-11eb-9d65-004dd52e164f.png)
![3](https://user-images.githubusercontent.com/28965732/97305477-24ac8300-1883-11eb-8394-b4a9a59947a3.png)
![5](https://user-images.githubusercontent.com/28965732/97305348-fb8bf280-1882-11eb-87f4-6c81c148c995.png)
![4](https://user-images.githubusercontent.com/28965732/97305404-0cd4ff00-1883-11eb-8516-95b17e3eec9e.png)



# Model evaluation

I evaluated the model using BLEU score.
Attention model achieved the highest 0.29 BLEU-4 score.
|MODELS|BLEU-1|BLEU-2|BLEU-3|BLEU-4|
|------|------|------|------|------|
|Unconditional Encoder-Decoder|0.44|0.30|0.23|0.13|
|Conditional Encoder-Decoder|0.58|0.41|0.31|0.23|
|Encoder-Decoder with Attention|**0.62**|**0.47**|**0.37**|**0.29**|

# Comparison of our Attention model with Google Translator

I also compared our trained Attention model with Google Translator. Our model performed really well compared to Google Translator for short sentences. Here are few examples.

|SOURCE|PREDICTED|GOOGLE TRANSLATOR|
|------|------|------|
|we should help tom|**wir sollten tom helfen**|wir sollten tom helfen|
|do you want to live in boston|willst du in boston wohnen|willst du in boston leben|

