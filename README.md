# Fair Influence Maximization Through Adversarial Network Embedding

This repository contains the implementation code and the data used in the paper, "Adversarial Graph Embeddings for Fair Influence Maximization over Social Networks". 

## The Model Architecture
The model consists of an auto-encoder which is adversarially trained with a discriminator. 
<p align="center">
![image](https://user-images.githubusercontent.com/35867461/77394182-d0c05400-6df2-11ea-8d54-8a7167d23753.png)
<p>
### The Encoder Architecture
The encoder consists of three dense layers followed by relu activations. The size of the encoder layers are sorted in a reverse order. Please refer to the code to see more details.
