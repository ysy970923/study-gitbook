# Others

## Other fields in Artificial Intelligence (Explainable AI, Compression, ...)

### Axiomatic Attribution for Deep Networks ([ICML 2017](https://arxiv.org/pdf/1703.01365.pdf))

* problem: existing attribution methods violate either of the two axioms
* goal: Integrated Gradients, new attribution method
* attribution method: understand the input-output behavior of the deep network
* two axioms:
  * Sensitivity:
    * if input, baseline differs one feature that have different predictions, the differing feature should be given non-zero attribution
    * Gradients violate Sensitvity
      * prediction function may flatten the input leading to zero gradient
  * Implementation Invariance:
    * networks are "functionally equivalent" if output is same for every input despite implementations
*   Integrated Gradients:

    [![](https://github.com/ysy970923/study/raw/main/images/integrated\_gradients.PNG)](https://github.com/ysy970923/study/blob/main/images/integrated\_gradients.PNG)
* remark: highly used in recent researches

### Similarity of Neural Network Representations Revisited ([ICML 2019](https://arxiv.org/pdf/1905.00414.pdf))

* problem:

### Understanding Deep Learning requires Rethinking Generalization ([ICLR 2017](https://dl.acm.org/doi/pdf/10.1145/3446776))

* contribution:
  * role of regularization (explicit and implicit)
  * finite sample expressivity
* effective capacity of neural networks
  * randomized datasets(random labels, random pixels...) take more steps to converge
  * **But they converge at some point**
* role of regularization
  * confine learning to a subset of the hypothesis space with manageable complexity
  * Explicit Regularization (augmentation, weight decay, dropout...)
    * seem to play **different role** (fit random training set well)
    * though helpful, changing model architecture is much better
  * Implicit Regularization (early stopping, BatchNorm)
    * also though helpful, seems to be not fundamental
* finite-sample expressivity
  * previous works: "population level", focused on representing entire domain
  * expressive power of neural networks on finite sample
    * even 2 layer network can represent any function of input sample (with RELU and 2n+d weights)
* Implicit regularization on linear models
  * convex models, simply solving gaussian kernel has good performance
  * adding implicit regularization gets better performance
  * but minimum norm might be bigger (does not predict generalization performance)
* remark: not sure if I understood well

### Contrastive Loss

* used for **unlabeled data**
* minimize distance between embedding vectors of positive pair, maximize distance between embedding vectors of negative pair
* L = (1-Y)_D^2 + Y_{max(0, m-D)}^2 (Y = 0(positive), 1(negative))

### DEEP COMPRESSION: COMPRESSING DEEP NEURAL NETWORKS WITH PRUNING, TRAINED QUANTIZATION AND HUFFMAN CODING ([ICLR 2016](https://arxiv.org/pdf/1510.00149.pdf))

* concept: Compress Neural Network

### Agree to Disagree: Diversity Through Disagreement for Better Transferability ([ICLR 2023](https://openreview.net/pdf?id=K7CbYQbyYhY))

* Mitigate Simplicity loss by disagreeing with the simple ERM solution model.
* Train with additional loss that indicates agreement on OOD data(OOD data is unlabeled)

### Towards Understanding Ensemble, Knowledge Distillation and Self-Distillation in Deep Learning ([ICLR 2023](https://openreview.net/pdf?id=Uuf2q9TfXGA))

* Why is ensemble good even though all the sub models are already train accuracy 100%?
* How can the ensemble knowledge be later distilled into a single neural network?
* Explanation through NTK is not enough. (Random feature mapping, Enlarging the feature space)
  * Training average works even better
  * Knowledge Distillation does not work.
* Multi-View Data Distribution
  * Individual Models pick up only single feature and memorize the remaining as the noise without learning any new features.
* Ensemble will allow the model to see multiple features.
