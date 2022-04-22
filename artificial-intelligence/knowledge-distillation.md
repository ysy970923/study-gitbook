# Knowledge Distillation

### On the Efficacy of Knowledge Distillation ([ICCV 2019](https://openaccess.thecvf.com/content\_ICCV\_2019/papers/Cho\_On\_the\_Efficacy\_of\_Knowledge\_Distillation\_ICCV\_2019\_paper.pdf))

* concept: Bigger model teachers are not always better teachers
* goal: better KD
* idea:
  * early stopping KD
  * sequential KD
  * early stopped teachers are better
* personal opinion: teachers to complex than students are actually bad teachers

### Understanding and Improving Knowledge Distillation ([arxiv](https://arxiv.org/pdf/2002.03532))

* goal: What is KD effect
* KD effects:
  * label smoothing
  * domain knowledge of class relationships (Like class 7 and class 2 in MNIST dataset)
  * gradient rescaling based on teachers measurement of instance difficulty
* personal opinion: all 3 effects are important

### Data-Free Knowledge Distillation for Deep Neural Networks ([ICCV 2019](https://openaccess.thecvf.com/content\_ICCV\_2019/papers/Chen\_Data-Free\_Learning\_of\_Student\_Networks\_ICCV\_2019\_paper.pdf))

* goal: Knowledge Distillation without access to data
* idea: use Activation layer statistics as metadata to reconstruct dataset for distillation
* personal opinion: isn't deep inversion like better?? This idea need additional metadata, can lead to privacy issues

### Online Knowledge Distillation with diverse peers ([AAAI 2020](https://arxiv.org/pdf/1912.00350.pdf))

* goal: Better online Knowledge Distillation
* Online Distillation?: no pre-trained teacher
* ONE (online distillation native on the fly) problems:
  * forcing to learn from same target(ensemble output)
  * hurts diversity
* idea: two level distillation
  1. self attention based targets for distillation
  2. ensemble output for distillation to group leader(groups student model)
* diversity between models can be maintained

### Relational Knowledge Distillation ([CVPR 2019](https://openaccess.thecvf.com/content\_CVPR\_2019/papers/Park\_Relational\_Knowledge\_Distillation\_CVPR\_2019\_paper.pdf))

* goal: Better Knowledge Distillation
* idea:
  * Conventional KD: loss between each sample's soft labels
  * Relational KD: loss between relational functions
* transferring structural knowledge using mutual relations of data example
* RKD-D, RKD-A (relational function type)
* better when used with conventional KD

### Be Your Own Teacher: Improve the Performance of Convolutional Neural Networks via Self Distillation ([ICCV 2019](https://openaccess.thecvf.com/content\_ICCV\_2019/papers/Zhang\_Be\_Your\_Own\_Teacher\_Improve\_the\_Performance\_of\_Convolutional\_Neural\_ICCV\_2019\_paper.pdf))

* goal: Why use complex teacher model? Use single model. (resource limited edge device)
* Adaptive Computation
* Deep Supervision
* idea: Knowledge distillation between shallow classifiers(low level blocks) and whole model
  * loss 1: CE loss with true label
  * loss 2: Knowledge Distillation with KL loss between whole model output
  * loss 3: L2 loss between block features (got idea from FITNET)
* personal opinion: better performance than conventional KD, but seems to have room for improvement
* must check [github](https://github.com/ArchipLab-LinfengZhang/pytorch-self-distillation-final) for detail implementations (not in paper)
* bottleneck structure different from paper
  * paper: no detail explaination about structure
  * github: use 1 sepconv layer (basic block in separable convolution way??) instead of 1 resnet block

### Towards Understanding Ensemble, Knowledge Distillation, and Self-Distillation in Deep Learning ([Microsoft](https://www.microsoft.com/en-us/research/blog/three-mysteries-in-deep-learning-ensemble-knowledge-distillation-and-self-distillation/))

* goal: get Answers to Three mysteries in deep learning: Ensemble, knowledge distillation, and self-distillation
* Ensemble, Why work?: Multi view approach
* Knowledge distillation: Forcing an individual model to learn multiple views
* Self distillation: Implicitly combining ensemble and knowledge distillation (shallow classifiers work as an ensemble)
* personal opinion: Didn't understand fully

### Knowledge Distillation Meets Self-Supervision ([ECCV 2020](https://www.ecva.net/papers/eccv\_2020/papers\_ECCV/papers/123540562.pdf))

* goal: propose SSKD framework better than other KD methods
* Contrastive learning, self supervised learning
* reading...

### Revisiting Knowledge Distillation via Label Smoothing Regularization ([CVPR 2020](https://openaccess.thecvf.com/content\_CVPR\_2020/papers/Yuan\_Revisiting\_Knowledge\_Distillation\_via\_Label\_Smoothing\_Regularization\_CVPR\_2020\_paper.pdf))

* goal: prove KD is a type of learned label smoothing regularization
* contribution: propose Teacher-free Knowledge Distillation (TfKD)
* reversed KD: KD from pretrained smaller model as teacher
* Defective KD: KD from poorly trained model as teacher
* Label Smoothing Regularization:
  * label smoothing: q′(k) = (1 − α)q(k) + αu(k), (usually u(k) = 1/K)
  * H(q′, p) =(1 − α)H(q, p) + α(D\_KL(u, p) + H(u))
  * L\_LS = (1 − α)H(q, p) + αD\_KL(u, p)
  * similar to KD equation (L\_KD = (1 − α)H(q, p) + αDKL(pt\_τ, p\_τ ).)
* Teacher-free Knowledge Distillation
  * TfKD\_self: KD from same model structure pretrained
  * TfKD\_reg: use LSR as a virtual teacher model
    * different from LSR as τ >> 1

### Deep Mutual Learning ([CVPR 2018](https://openaccess.thecvf.com/content\_cvpr\_2018/papers/Zhang\_Deep\_Mutual\_Learning\_CVPR\_2018\_paper.pdf))

* concept: No pretrained teacher model, pool of untrained students learn together?
* Loss term:
  * L\_Θ1 = L\_C1 + D\_KL(p\_2|p\_1)
  * L\_Θ2 = L\_C2 + D\_KL(p\_1|p\_2).
* can be extended to more than 2 networks
* why work:
  * different init conditions, probs vary
  * increase student's posterior entropy
  * converge to a more robust(flatter) minima
* points to note:
  * ensemble teacher better?: learning from ensemble teacher was worse than learning each peers one by one
  * models become similar?: logits become similar, but aligning internal representations(such as features) diminish cohort diversity, damage ability of each network to teach
  * semi-supervised learning: can be well used in semi supervised learning (subset of labelled data)

### FITNETS: Hints For Thin Deep Nets ([ICLR 2015](https://arxiv.org/pdf/1412.6550.pdf))

* goal: transfer teacher knowledge to deeper (and thinner) student
* idea: student's "guided layer" output learns from teacher's "hint layer" output
* add a regressor to a guided layer to match the size of the hint layer
* 2 stage process:
  1. minimize L2 loss between hint layer output and guided layer output(with regressor)
  2. Knowledge Distillation from teacher to student model
* points to note:
  * after Resnet, training deep networks became easier (so use of training deep networks faded)
  * can be used additionally to KD (as in self-distillation)\\
