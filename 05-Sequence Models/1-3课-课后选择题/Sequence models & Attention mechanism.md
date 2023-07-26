1. Consider using this encoder-decoder model for machine translation.
![Image 1](img/1.png)
This model is a “conditional language model” in the sense that the encoder portion (shown in green) is modeling the probability of the input sentence *x*.

    - [ ] True
    - [x] False

2. In beam search, if you increase the beam width BB, which of the following would you expect to be true? Check all that apply.
    - [x] Beam search will run more slowly
    - [x] Beam search will use up more memory.
    - [x] Beam serach will generally find better solutions(i.e. do a better job maximizing *P(y|x)*)
    - [ ] Beam search will converge after fewer steps.
          
> As the beam width decreases, beam search runs more quickly, uses up less memory, and converges after fewer steps, but will generally not find the maximum P(y|x).

3. In machine translation, if we carry out beam search `without` using sentence normalization, the algorithm will tend to output overly `short` translations.

    - [x] True
    - [ ] False

4. Suppose you are building a speech recognition system, which uses an RNN model to map from audio clip xx to a text transcript yy. Your algorithm uses beam search to try to find the value of yy that maximizes P(y∣x). 
On a dev set example, given an input audio clip, your algorithm outputs the transcript 
y = “I’m building an A Eye system in Silly con Valley.”, whereas a human gives a much superior transcript 
y\* = “I’m building an AI system in Silicon Valley.”
According to your model,
P(y|x) = 1.09 * 10<sup>-7</sup>
P(y|x) = 7.21 * 10<sup>-8</sup>
Would you expect increasing the beam width B to help correct this example?



    - [x] No, because P(y\*|x) ≤ P(y|x) indicates the error should be attributed to the RNN rather than to the search algorithm.
    - [ ] No, because P(y\*|x) ≤ P(y|x) indicates the error should be attributed to the search algorithm rather than to the RNN.
    - [ ] Yes, because P(y\*|x) ≤ P(y|x) indicates the error should be attributed to the RNN rather than to the search algorithm.
    - [ ] Yes, because  P(y\*|x) ≤ P(y|x) indicates the error should be attributed to the search algorithm rather than to the RNN.
      
    >  P(y\*|x) > P(y|x) indicates the error should be attributed to the search algorithm rather than to the RNN.

5. Continuing the example from Q4, suppose you work on your algorithm for a few more weeks, and now find that for the vast majority of examples on which your algorithm makes a mistake, P(y\*|x) > P(y|x) This suggest you should focus your attention on improving the search algorithm `not RNN`.

    - [x] True
    - [ ] False

6. Consider the attention model for machine translation.
![Model](img/6_1.png)
Further, here is the formula for α<sup><t,t’></sup>.
![equation](img/6_2.png)
Which of the following statements about α<sup><t,t’></sup> are true? Check all that apply.

    - [x] We expect  α<sup><t,t’></sup> to be generally larger for values of a<t> that are highly relevant to the value the network should output for y<t>. (Not  y<sup><t’></sup>)
    - [ ] We expect  α<sup><t,t’></sup> to be generally larger for values of a<sup><t></sup> that are highly relevant to the value the network should output for y<sup><t’></sup>. (Note the indices in the superscripts.)
    - [x] ∑<sub>t</sub> α<sup> <t,t’></sup> is equal to the amount of attention y<sup><t’></sup> should pay to a<sup><t’></sup>
    - [x] ∑<sub>t'</sub> α<sup> <t,t’></sup> =1 (Note the summation is over t'.)
    
7. The network learns where to “pay attention” by learning the values e<sup><t,t’></sup>, which are computed using a small neural network: We can't replace s<sup><t−1></sup> with s<sup>t</sup> as an input to this neural network. This is because s<sup><t></sup> depends on α<sup><t,t’></sup> which in turn depends on e<sup><t,t’></sup> ; so at the time we need to evalute this network, we haven’t computed s<sup><t></sup> yet.
    
    - [x] True
    - [ ] False

8. Compared to the encoder-decoder model shown in Question 1 of this quiz (which does not use an attention mechanism), we expect the attention model to have the greatest advantage when:

    - [x] The input sequence length T<sub>x</sub> is large.
    - [ ] The input sequence length T<sub>x</sub> is small.

9. Under the CTC model, identical repeated characters not separated by the “blank” character (_) are collapsed. Under the CTC model, what does the following string collapse to?
__c_oo_o_kk___b_ooooo__oo__kkk

    - [ ] cokbok
    - [x] cookbook
    - [ ] cook book
    - [ ] coookkboooooookkk

    > The basic rule for the CTC cost function is to collapse repeated characters not separated by "blank". If a character is repeated, but separated by a “blank”, it is included in the string.
    
10. In trigger word detection, x<sup><t></sup> is:

    - [x] Features of the audio (such as spectrogram features) at time t.
    - [ ] The tt-th input word, represented as either a one-hot vector or a word embedding.
    - [ ] Whether the trigger word is being said at time t.
    - [ ] Whether someone has just finished saying the trigger word at time t.

> In trigger word detection, if the target label for x<sup><t></sup> is 1: whether or not a trigger word has been said.


11. The attention model performs the same as the encoder-decoder model, no matter the sentence length?
> False
> The performance of the encoder-decoder model declines as the amount of words increases. The attention model has the greatest advantage when the input sequence length Tx is large.

12. In trigger word detection, x<sup><t></sup> represents the trigger word x being stated for the t-th time.
> True





Transformer

1. A Transformer Network, unlike its predecessor RNNs, GRUs, and LSTMs, can process entire sentences all at the same time.
> True

2. The major innovation of the transformer architechture is combining the use of LSTMs and RNN sequential processing.
> False
> The major innovation of the transformer architecture is combining the use of attention based representations and a CNN convolutional neural network style of processing. To revise the concept watch the lecture .

3. What are the key inputs to computing the attention value for each word.
> the key inputs to computing the attention value for each word are called the query, key and value.

4. What letter dose the ? represent in attention(Q,K,V) = softmax[ QK^T / (d?)^0.5 ] V?
> k

5. Are the following statements true regarding
Query(Q) = interesting questions about the words in a sentence
Key(K) = qualities of words given a Q
Value(V) = specific representations of words given a Q
> True

6. what does i represent in this multi-head attention computation?
The computed attention weight matrix associated with nnn

7. decoder second block of multi-head attention?
feed forward neural network, mutil-head attention

8. Following is the architecture within a Transformer Network.
what dose the output of the encoder block contain?
> contextual semantic embedding and positional encoding information

10.which of the following is a good criterion for a good positional encoding algorithm?
Distance between any two time-steps should be consistent for all sentence lengths.
The algorithm shoudl be able to generalize to longer sentences.
