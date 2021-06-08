# summarizer
# problem statement:
In this covid lockdown everything is going in online from meetings to classes for students it's a kind of all day busy schedule for everyone to help the students to get an intuative idea about what are the main things tought in class or meeting.
# idea of approach:
we need an application or an API to convert the vedio into text and then using that text document we can use Google's BERT Summarizer which helps to summarize the document and helps people to go through the text in no time.
# AWS Transcribe:
Amazon Transcribe makes it easy for developers to add speech to text capabilities to their applications. Audio data is virtually impossible for computers to search and analyze. Therefore, recorded speech needs to be converted to text before it can be used in applications. Historically, customers had to work with transcription providers that required them to sign expensive contracts and were hard to integrate into their technology stacks to accomplish this task. Many of these providers use outdated technology that does not adapt well to different scenarios, like low-fidelity phone audio common in contact centers, which results in poor accuracy.
Amazon Transcribe uses a deep learning process called automatic speech recognition (ASR) to convert speech to text quickly and accurately.
# Google BERT Summarizer:
it's a state-of-art model developed by the google for extractive summarization.
BERT models are pre-trained on huge datasets thus no further training is required.
It uses a powerful flat architecture with inter sentence tranform layers so as to get the best results in summarization.
# advantages of BERT :
It is most efficient summarizer till date.
Faster than RNN.
# BERT Architecture:
# BERT base
In the BERT base model we have 12 transformer layers along with 12 attention layers and 110 million parameters.
# BERT Large
In BERT large model we have 24 transformer layers along with 16 attention layers and 340 million parameters.
# Transformer layer:
Tranformer layer is actually a combination of complete set of encoder and decoder layers and the intermediate connections. Each encoder includes Attention layers along with a RNN. Decoder also has the same architecture but it includes another attention layer in between them as does the seq2seq model. It helps to concentrate on important words.
# Summarization layers:
The one major noticable difference between RNN and BERT is the Self attention layer. The model tries to identify the strongest links between the words and thus helps in representation.

We can have different types of layers within the BERT model each having its own specifications:

Simple Classifier - In a simple classifier method , a linear layer is added to the BERT along with a sigmoid function to predict the score Yˆi.

Yˆi = σ(WoTi + bo)
Inter Sentence Transformer - In the inter sentence transformer ,simple classifier is not used. Rather various transformer layers are added into the model only on the sentence representation thus making it more efficient. This helps in recognizing the important points of the document.

h˜l = LN(hl-1 + MHAtt(hl-1)
hl = LN(h˜l + FFN(h˜l))
where h0 = PosEmb(T) and T are the sentence vectors output by BERT, PosEmb is the function of adding positional embeddings (indicating the position of each sentence) to T, LN is the layer normalization operation, MHAtt is the multi-head attention operation and the superscript l indicates the depth of the stacked layer.
These are followed by the sigmoid output layer

Yˆi = σ(WohLi + bo)
hL is the vector for senti from the top layer (the L-th layer ) of the Transformer.

Recurrent Neural network - An LSTM layer is added with the BERT model output in order to learn the summarization specific features. Where each LSTM cell is normalized. . At time step i, the input to the LSTM layer is the BERT output Ti.
Ci = σ(Fi).Ci-1+ σ(Ii).tanh(Gi-1)
hi =σ(Ot).tanh(LNc(Ct))
where Fi, Ii, Oi are forget gates, input gates,
output gates; Gi is the hidden vector and Ci is the memory vector, hi is the output vector and LNh, LNx, LNc are there difference layer normalization operations. The output layer is again the sigmoid layer.
