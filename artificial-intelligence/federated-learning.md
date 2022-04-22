---
cover: >-
  https://images.unsplash.com/photo-1519389950473-47ba0277781c?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=2970&q=80
coverY: 0
---

# Federated Learning

### Adaptive Federated Optimization ([ICLR 2021](https://github.com/ysy970923/study/blob/main/AI))

* problem: standard federated optimization methods have problems, use adaptive optimization methods like methods in non-federated learning
* FedOpt: ClientOpt, ServerOpt
* propose adaptive methods for ServerOpt, compare with non-adaptive methods
  * FedADAGRAD, FedYOGI, FedADAM
  *

### No Fear of Heterogeneity: Classifier Calibratoin for Federated Learning with Non-IID Data ([NIPS 2021](https://proceedings.neurips.cc/paper/2021/file/2f2b265625d76a6704b08093c652fd79-Paper.pdf))

* problem: previous works handling non-IID data lacks deep understading of how data heterogeneity affects each layers.
* goal: analysis on each layers, CCVR(Classifier Calibration with Virtual Representations)
* The Devil Is In Classifier
* CKA similarity: ...

### What Do We Mean By Generalization In Federated Learning? ([ICLR 2022](https://openreview.net/pdf?id=VimqQq-i\_Q))

* problem: performance gaps from unseen client distributions(participation gaps) should be considered
* goal: three-way split for measurement, Observe participation gaps, semantic partitioning
* Why is participation gaps important?
  * quantify client diversity
  * quantify incentive for clients to participate
  * measure overfitting on the population distribution
  * quantify model robustness to unseen clients
* partitioning matters (data)
  * Natural partitioning (like emnist) represents client heterogeneity better than label-based partitioning
  * Sementic Client Partitioning
    * close to natural partitioning in centralized dataset
* personal opinion: new approach, but iffy about the situation

### Sageflow: Robust Federated Learning against Both Stragglers and Adversaries ([NIPS 2021](https://proceedings.neurips.cc/paper/2021/file/076a8133735eb5d7552dc195b125a454-Paper.pdf))

* problem: Adversaries and Stragglers damage performance
* goal: Sageflow, Entropy-Based filtering and Loss-Weighted Averaging [![](https://github.com/ysy970923/study/raw/main/images/sageflow\_1.PNG)](https://github.com/ysy970923/study/blob/main/images/sageflow\_1.PNG)
* method:
  * Entropy-Based Filtering:
    * use server public data to get Entropy of the model (using probability of prediction of each classes)
    * filter models above threshold (leave low entropy, high confidence)
    * effective for model poison attacks
    * less effective for data poison such as label switching
  * Loss-Weighted Averaging:
    * use server public data to get Loss of the model
    * weight inverse to loss (less loss -> higher weight)
    * effective for data poison attacks
  * Both methods are complementary
* personal opinion: using public data can be a limitation in federated learning

### Efficient Split-Mix Federated Learning For On-Demand and In-Situ Customization ([ICLR 2022](https://openreview.net/pdf?id=\_QLmakITKg))

* problem: Heterogeneous computational budgets
* goal: Split-Mix, shatter complete knowledge into smaller pieces and customize flexible formations of pieces (model size & robustness)

[![](https://github.com/ysy970923/study/raw/main/images/splitmix\_1.PNG)](https://github.com/ysy970923/study/blob/main/images/splitmix\_1.PNG)

* mehod:
  *   Customize Model Size:

      * SHeteroFL: HeteroFL with training all affordable prototypes locally
      * slimmer network -> extract less feature -> generalizes poorly
      * less data (compare SHeteroFL with FedAvg) -> features are less generalizable
      * Diverse base models, ensemble

      [![](https://github.com/ysy970923/study/raw/main/images/splitmix\_2.PNG)](https://github.com/ysy970923/study/blob/main/images/splitmix\_2.PNG)
  * Customize Adversarial Robustness
    * Adverarial Training (Madry et al., 2018) is used to improve adversarial Robustness
    * Share parameters except BN layer between Standard Training Model and Adversarial Training Model
      * Maximize robustness and accuracy by expertised BNs (Xie & Yulle, 2019; Xie et al., 2020)
    * Layer-wise Mixing (BN):
      * averaging final output: fowarding memory doubled
      * weighted-averaging of each BN layers\
        \\

### Federated Learning Based On Dynamic Regularization ([ICLR 2021](https://openreview.net/pdf?id=B7v4QMR6Z9w))

* problem: In FL situation, Global optima is different from each Local optima
*   goal: FedDyn, Dynamic regularization method to ensure Local optima is consistent with Global optima

    [![tmp](https://user-images.githubusercontent.com/57357447/130954953-010a5208-1a84-44e9-87c6-4512847b8ccf.PNG)](https://user-images.githubusercontent.com/57357447/130954953-010a5208-1a84-44e9-87c6-4512847b8ccf.PNG)

    [![tmp2](https://user-images.githubusercontent.com/57357447/130955180-73b6b8f5-5dd4-4af0-ad30-cf4304e0db90.PNG)](https://user-images.githubusercontent.com/57357447/130955180-73b6b8f5-5dd4-4af0-ad30-cf4304e0db90.PNG)

    [![image](https://user-images.githubusercontent.com/57357447/130955251-a1ca4d4e-0f5a-461f-8fde-2c6567723592.png)](https://user-images.githubusercontent.com/57357447/130955251-a1ca4d4e-0f5a-461f-8fde-2c6567723592.png)
* faster convergence, higher performance than other SOTA methods
* personal opinion: mathematically proven method, good performance in experiment
* personal implementation(not ready)

### HeteroFL: Computation And Communication Efficient Federated Learning For Heterogeneous Clients ([ICLR 2021](https://openreview.net/pdf?id=TNkPBBYFkXg))

* problem: Heterogenous clients are equipped with various resource capabilities
* goal: HeteroFL (train heterogenous local models, produce single global inference model)
* contributions:
  * Heterogenous models: vary the width of hidden channels
  * Static Batch Normalization: do not track running statistics at train time, query to local clients after train process
  * Scaler: like dropout, scale to match inference
* personal opinion: important concept and goal, experiment results are controversial (can see in open review)
* personal implementation(not ready)

### Group Knowledge Transfer: Federated Learning of Large CNNs at the Edge ([NIPS 2020](https://proceedings.neurips.cc/paper/2020/file/a1d4c20b182ad7137ab3606f0e3fc8a4-Paper.pdf))

* problem: edge nodes have computational limitation
* goal: Group Knowledge Transfer (FedGKT) [![image](https://user-images.githubusercontent.com/57357447/131290944-0657b0ac-ca2d-4f9b-8c06-4166fef80752.png)](https://user-images.githubusercontent.com/57357447/131290944-0657b0ac-ca2d-4f9b-8c06-4166fef80752.png)
* contribution:
  * Split learning like: like split learning offloading big model computation to server tackles edge nodes limitations
  * Group Knowledge Transfer: new way of knowledge transfer
* discussion:
  * privacy: can get raw data from feature map
  * communication cost: depends on number of data points (cost can be larger than transferring model or gradient)
* personal opinion: FL is used mainly due to privacy issues, but it seems in this way raw data can be achieved from feature maps

### Ensemble Distillation for Robust Model Fustion in Federated Learning ([NIPS 2021](https://proceedings.neurips.cc/paper/2020/file/18df51b97ccd68128e994804f3eccc87-Supplemental.pdf))

* problem: In classic FL algorithms, client models have to be same size and structure
* contribution: FedDF
  * can allow to combine multiple heterogenous weak classifiers
  * can use unlabeled data or artificially generated data (like GAN)
* FedDF:
  1. FedAvg single round
  2. KD with data (unlabeled or by generator) Knowledge ditillation with ensemble of local models as teacher, server model as server student
* Experiment detail (in paper): cifar-100, Imagenet(downsampled) was used as distillation dataset
* Understanding FedDF:
  * ensembling and KD via "out-of-domain data"
  * realistic data: distillating with random noise makes worse
  * data fraction: only 1% data (of local training dataset) result in reasonably good fusion performance
* personal opinion:
  * if enough distillation data, robust algorithm
  * but I think relation between distillation data and target data seems to be studied more

### Federated Optimization for Heterogeneous Networks ([MLSys 2020](https://proceedings.mlsys.org/paper/2020/file/38af86134b65d0f10fe33d30dd76442e-Paper.pdf))

* problem: In non-iid settings, FedAvg lacks convergence
* contribution: FedProx
  * add proximal term
  * provide convergence guarantees, in highly hetero settings (acc improves upto 22%)
*   proximal term:

    [![image](https://user-images.githubusercontent.com/57357447/131327679-7aef3a39-6200-405d-9b37-8e7c8401d427.png)](https://user-images.githubusercontent.com/57357447/131327679-7aef3a39-6200-405d-9b37-8e7c8401d427.png)

    * restricting local updates to be closer to global model
    * allows for safely incorporating variable amounts of local work resulting from systems heterogeneity
* remark:
  * personally think works well because terms are similar to FedDyn terms
  * more non-iid(data heterogeneity), better improvement

### FedSplit: An algorithmic framework for fast federated optimization ([NIPS 2020](https://arxiv.org/pdf/2005.05238.pdf))

* problem: most FL algorithms fail to preserve toe fixed points of the original optimization problem
* contribution: FedSplit, guarantees optimal solution to the original problem [![image](https://user-images.githubusercontent.com/57357447/131475805-e1d4f8d7-e7f2-403e-aaef-4f75536518e0.png)](https://user-images.githubusercontent.com/57357447/131475805-e1d4f8d7-e7f2-403e-aaef-4f75536518e0.png)
* proximal terms from FedProx are used
* local models remains seperately from global model
* personal opinion:
  * all proofs are in the paper
  * experiments were held on least squares and logistic regression, but not on deep neural networks
  * experiment on deep neural networks seems to be needed

### Federated Learning with Only Positive Labels ([ICML 2020](https://arxiv.org/pdf/2004.10342.pdf))

* problem: FL setup where user has only access to single class
* contrastive loss: pos, neg losses differ
* problem: only have positive samples (single class per client)
* FedAwS:
  * spreadout regularizer:
    * server performs additional optimization step for seperation of class embeddings
  * stochastic negative mining:
    * modified version of spreadout regularizer

### Towards Model-Agnostic Federated Learning Using Knowledge Distillation

* Use Knowledge Distillation among different models
* Predict soften labels of the train data from model trained by other client
* Use the soften labels to KD with training the model of the client
* kernel regression framework
* theoretical
* data heterogeneity & KD can't be together
