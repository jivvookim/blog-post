---
type: docs
bookToc: True
weight: 1
---

# Better & Faster Large Language Models via Multi-token Prediction
*Posted by Jinoh Cho and Seonghyeon Park*
- Authors: Gloeckle et al. 
- Institution : FAIR at Meta, CERMICS Ecole des Ponts ParisTech and LISN Universite Paris-Saclay
  
  
# Preliminaries

### Language Modeling and Next-Token Prediction Task

Learning through a next-token prediction task has been a mainstream for language modeling. The goal of a next-token prediction task is to maximize the probability of the next token $x_{t+1}$, given the history of previous tokens $x_{t:1} = x_1, \ldots, x_t$. This can be formulated as follow:

$$ 
L_1 = - \sum_{t} \log P_{\theta}(x_{t+1} \mid x_{t:1}), 
$$

where $P_{\theta}$ represents large language model under training. 

# Core Idea

### Multi-Token Prediction Task 

In this work, authors propose to learn language modeling from a multi-token prediction rather than a next-token prediction. At each position of the training corpus, the model is instructed to predict $n$ future tokens at once. Thus, the training objective is changed as follow:

$$
L_n = - \sum_{t} \log P_{\theta}(x_{t+n:t+1} \mid x_{t:1}) = - \sum_{t}\sum_{i=1}^{n} \log P_{\theta}(x_{t+i} \mid x_{t:1}). 
$$

### Memory-Efficient Implementation
Directly training language models by minimizing the multi-token prediction loss could result in high GPU memory usage, severly limiting the allowable batch-size. Thus, authors propose to carefully adapt the sequence of forward and backward operations for each prediction head rather than operating forward and backword operations simultaneusly for all heads. This could result in reducing peak GPU memory usage $O(nV+d)$ into $O(V+d)$. Here, the $n$ and $V$ denote the number of head and vocabulary size, respectively. Note that $d$ is the vector dimension of shared transformer trunk. 

<p align="center">
    <img src='./Memory Efficient.png' width="450">
</p>

### Faster Inference with Self-speculative Decoding


# Result

# Why does it work?

# Conclusion

# Discussion
