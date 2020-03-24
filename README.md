# Fair Influence Maximization Through Adversarial Network Embedding

This repository contains the implementation code and the data used for the paper, "Adversarial Graph Embeddings for Fair Influence Maximization over Social Networks". 

## The Model Architecture
The model consists of an auto-encoder which is adversarially trained with a discriminator. 
![image](https://user-images.githubusercontent.com/35867461/77394182-d0c05400-6df2-11ea-8d54-8a7167d23753.png)
### The Auto-Encoder Architecture
The encoder consists of three dense layers followed by relu activations. The size of the encoder layers are sorted in a reverse order. The decoder has the exact reverse architecture, and the final has a sigmoid activation instead of a relue activation. The auto-encoder model is first pre-trained for 300 epochs and then adversarially trained with the discriminator for 500 epochs. Please refer to the code for more details.

### The Discriminator Architecture
Discriminator consists of four dense layers with relu activations (except for the output layer that has a sigmoid activation) that is also followed by a droupout. The disciriminator is pre-trained for 50 epochs and then adversarially trained with the auto-encoder for 500 epochs. Please refer to the code for more details.
