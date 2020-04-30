# Fair Influence Maximization Through Adversarial Network Embedding

This repository contains the implementation code and the data used for the paper, "Adversarial Graph Embeddings for Fair Influence Maximization over Social Networks". 

## The Model Architecture
The model consists of an auto-encoder which is adversarially trained with a discriminator. The goal of the adversarial training is to obtain embeddings for nodes of both communities that are indistinguishable by the discriminator. To achieve this we make the
embedder to incur a loss if it generates embeddings that can be discriminated with high confidence by the discriminator. This
means that we make the embedder to change the distribution of embeddings of a community to be close to the distribution of the embeddings of the other community. When the two distributions get close, the discriminator can no longer distinguish between the embeddings of the two communities with high confidence. Meanwhile, the discriminator will incur a loss if it predicts the wrong label for the embeddings
of the two communities. 
![image](https://user-images.githubusercontent.com/35867461/77394182-d0c05400-6df2-11ea-8d54-8a7167d23753.png)
### The Embedder Architecture
The embedder that we use in our experiments is a standard auto-encoder which has three encoding and three decoding layers. Both of the encoding and decoding layers are Dense layers that are followed by a relu activation function, except for the final layer of the decoder which has a sigmoid activation function.  The auto-encoder model is first pre-trained for 300 epochs and then adversarially trained with the discriminator for 500 epochs. Please refer to the code for more details.

### The Discriminator Architecture
The discriminator that we use is also a neural network with four Dense layers where the first three layers have a relu activation and the final layer has a sigmoid activation function. The number of neurons at layers are (25, 15, 6, 1) respectively. The discriminator takes an embedding vector of 30 dimensions and turns it to a number between 0 and 1, where 0 means that the node belong to community A, and 1 means that the node belongs to community B. A number between 0 and 1, like 0.5 means that the discriminator is unsure about the community of the node. We pre-train the discriminator for 50 epochs to obtain a classification accuracy of 0.9999. After the pretraining, the discriminator is adversarially trained with the embedder for 300 epochs.
