---
layout: home
author_profile: true
toc: true
---

<h2 class="archive__title">{{ "What's New" }}</h2>

- Jan 2023: Our papers on "Federated Neural Bandit" and "Zeroth-Order Optimization" are accepted to ICLR 2023!
- Sep 2022: Our papers on "Training-free NAS" and "Neural Thompson Sampling" are accepted to NeurIPS 2022!
- May 2022: Our paper on "Neural Ensemble Search" is accepted to UAI 2022!
- May 2022: Our paper on "Data Valuation" is accepted to ICML 2022!
- Jan 2022: Our paper on "Training-free Neural Architecture Search" is accepted to ICLR 2022!

<h2 class="archive__title">{{ "Accepted Papers" }}</h2>
\# denotes corresponding author, * denotes equal contribution. 

<h4 class="archive__subtitle">{{ "2023" }}</h4>  

- <span style="color: royalblue">Zeroth-Order Optimization with Trajectory-Informed Derivative Estimation.</span>  
    **Yao Shu**\*, Zhongxiang Dai\*, Weicong Sng, Arun Verma, Patrick Jaillet and Bryan Kian Hsiang Low.  
    In *The 11th International Conference on Learning Representations* (**ICLR**), 2023  
    Acceptance rate: 31.8%. [[pdf](https://openreview.net/pdf?id=n1bLgxHW6jW)]  
    <details>
        <summary>Abstract</summary>
        Zeroth-order (ZO) optimization, in which the derivative is unavailable, has recently succeeded in many important machine learning applications. Existing algorithms rely on finite difference (FD) methods for derivative estimation and gradient descent (GD)-based approaches for optimization. However, these algorithms suffer from query inefficiency because additional function queries are required for derivative estimation in their every GD update, which typically hinders their deployment in applications where every function query is expensive. To this end, we propose a trajectory-informed derivative estimation method which only uses the optimization trajectory (i.e., the history of function queries during optimization) and hence eliminates the need for additional function queries to estimate a derivative. Moreover, based on our derivative estimation, we propose the technique of dynamic virtual updates, which allows us to reliably perform multiple steps of GD updates without reapplying derivative estimation. Based on these two contributions, we introduce the zeroth-order optimization with trajectory-informed derivative estimation (ZoRD) algorithm for query-efficient ZO optimization. We theoretically demonstrate that our trajectory-informed derivative estimation and our ZoRD algorithm improve over existing approaches, which is then supported by our real-world experiments such as black-box adversarial attack, non-differentiable metric optimization and derivative-free reinforcement learning.
    </details>  
- <span style="color: royalblue">Federated Neural Bandit.</span>  
    Zhongxiang Dai, **Yao Shu**, Arun Verma, Flint Xiaofeng Fan, Bryan Kian Hsiang Low and Patrick Jaillet.  
    In *The 11th International Conference on Learning Representations* (**ICLR**), 2023  
    Acceptance rate: 31.8%. [[pdf](https://openreview.net/pdf?id=38m4h8HcNRL)]  
    <details>
        <summary>Abstract</summary>
        Recent works on neural contextual bandits have achieved compelling performances due to their ability to leverage the strong representation power of neural networks (NNs) for reward prediction. Many applications of contextual bandits involve multiple agents who collaborate without sharing raw observations, thus giving rise to the setting of federated contextual bandits}. Existing works on federated contextual bandits rely on linear or kernelized bandits, which may fall short when modeling complex real-world reward functions. So, this paper introduces the federated neural-upper confidence bound (FN-UCB) algorithm. To better exploit the federated setting, FN-UCB adopts a weighted combination of two UCBs: UCB^a allows every agent to additionally use the observations from the other agents to accelerate exploration (without sharing raw observations), while UCB^b uses an NN with aggregated parameters for reward prediction in a similar way to federated averaging for supervised learning. Notably, the weight between the two UCBs required by our theoretical analysis is amenable to an interesting interpretation, which emphasizes UCB^a initially for accelerated exploration and relies more on UCB^b later after enough observations have been collected to train the NNs for accurate reward prediction (i.e., reliable exploitation). We prove sub-linear upper bounds on both the cumulative regret and the number of communication rounds of FN-UCB, and empirically demonstrate its competitive performance.
    </details>  


<h4 class="archive__subtitle">{{ "2022" }}</h4>  

- <span style="color: royalblue">Unifying and Boosting Gradient-Based Training-Free Neural Architecture Search.</span>  
    **Yao Shu**, Zhongxiang Dai, Zhaoxuan Wu, Bryan Kian Hsiang Low  
    In *The 36th Conference on Neural Information Processing Systems* (**NeurIPS**), 2022  
    Acceptance rate: 25.6%. [[pdf](https://arxiv.org/pdf/2201.09785.pdf)]  
    <details>
        <summary>Abstract</summary>
        Neural architecture search (NAS) has gained immense popularity owing to its ability to automate neural architecture design. A number of training-free metrics are recently proposed to realize NAS without training, hence making NAS more scalable. Despite their competitive empirical performances, a unified theoretical understanding of these training-free metrics is lacking. As a consequence, (a) the relationships among these metrics are unclear, (b) there is no theoretical interpretation for their empirical performances, and (c) there may exist untapped potential in existing training-free NAS, which probably can be unveiled through a unified theoretical understanding. To this end, this paper presents a unified theoretical analysis of gradient-based training-free NAS, which allows us to (a) theoretically study their relationships, (b) theoretically guarantee their generalization performances, and (c) exploit our unified theoretical understanding to develop a novel framework named hybrid NAS (HNAS) which consistently boosts training-free NAS in a principled way. Remarkably, HNAS can enjoy the advantages of both training-free (i.e., superior search efficiency) and training-based (i.e., remarkable search effectiveness) NAS, which we have demonstrated through extensive experiments.
    </details>  
- <span style="color: royalblue">Sample-Then-Optimize Batch Neural Thompson Sampling.</span>  
    Zhongxiang Dai, **Yao Shu**#, Bryan Kian Hsiang Low, Patrick Jaillet  
    In *The 36th Conference on Neural Information Processing Systems* (**NeurIPS**), 2022  
    Acceptance rate: 25.6%. [[pdf](https://arxiv.org/pdf/2210.06850.pdf)]  
    <details>
        <summary>Abstract</summary>
        Bayesian optimization (BO), which uses a Gaussian process (GP) as a surrogate to model its objective function, is popular for black-box optimization. However, due to the limitations of GPs, BO underperforms in some problems such as those with categorical, high-dimensional or image inputs. To this end, recent works have used the highly expressive neural networks (NNs) as the surrogate model and derived theoretical guarantees using the theory of neural tangent kernel (NTK). However, these works suffer from the limitations of the requirement to invert an extremely large parameter matrix and the restriction to the sequential (rather than batch) setting. To overcome these limitations, we introduce two algorithms based on the Thompson sampling (TS) policy named Sample-Then-Optimize Batch Neural TS (STO-BNTS) and STO-BNTS-Linear. To choose an input query, we only need to train an NN (resp. a linear model) and then choose the query by maximizing the trained NN (resp. linear model), which is equivalently sampled from the GP posterior with the NTK as the kernel function. As a result, our algorithms sidestep the need to invert the large parameter matrix yet still preserve the validity of the TS policy. Next, we derive regret upper bounds for our algorithms with batch evaluations, and use insights from batch BO and NTK to show that they are asymptotically no-regret under certain conditions. Finally, we verify their empirical effectiveness using practical AutoML and reinforcement learning experiments. 
    </details>  
- <span style="color: royalblue">Neural Ensemble Search via Bayesian Sampling.</span>  
    **Yao Shu**, Yizhou Chen, Zhongxiang Dai, Bryan Kian Hsiang Low  
    In *The 38th Conference on Uncertainty in Artificial Intelligence* (**UAI**), 2022  
    Acceptance rate: 32.3%. [[pdf](https://openreview.net/pdf?id=Bh4lBPUjqg9)]  
    <details>
        <summary>Abstract</summary>
        Recently, neural architecture search (NAS) has been applied to automate the design of neural networks in real-world applications. A large number of algorithms have been developed to improve the search cost or the performance of the final selected architectures in NAS. Unfortunately, these NAS algorithms aim to select only one single well-performing architecture from their search spaces and thus have overlooked the capability of neural network ensemble (i.e., an ensemble of neural networks with diverse architectures) in achieving improved performance over a single final selected architecture. To this end, we introduce a novel neural ensemble search algorithm, called neural ensemble search via Bayesian sampling (NESBS), to effectively and efficiently select well-performing neural network ensembles from a NAS search space. In our extensive experiments, NESBS algorithm is shown to be able to achieve improved performance over state-of-the-art NAS algorithms while incurring a comparable search cost, indicating the superior of our NESBS algorithm over these conventional NAS algorithms in practice. 
    </details>  
- <span style="color: royalblue">DAVINZ: Data Valuation using Deep Neural Networks at Initialization.</span>  
    Zhaoxuan Wu, **Yao Shu**, Bryan Kian Hsiang Low  
    In *The 39th International Conference on Machine Learning* (**ICML**), 2022  
    Acceptance rate: 21.9%. [[pdf](https://proceedings.mlr.press/v162/wu22j/wu22j.pdf)] 
    <details>
        <summary>Abstract</summary>
        Recent years have witnessed a surge of interest in developing trustworthy methods to evaluate the value of data in many real-world applications, e.g., collaborative machine learning, data marketplaces, etc. Existing data valuation methods typically valuate data using the generalization performance of converged machine learning models after their long-term model training, making data valuation on large complex deep neural networks (DNNs) unaffordable. To this end, we theoretically derive a domain-aware generalization bound to estimate the generalization performance of DNNs without model training. We then exploit this theoretically derived generalization bound to develop a novel training-free data valuation method named data valuation at initialization (DAVINZ) on DNNs, which consistently achieves remarkable effectiveness and efficiency in practice. Moreover, our training-free DAVINZ, surprisingly, can even theoretically and empirically enjoy the desirable properties that training-based data valuation methods usually attain, making it more trustworthy in practice. 
    </details>  
- <span style="color: royalblue">NASI: Label- and Data-agnostic Neural Architecture Search at Initialization.</span>  
    **Yao Shu**, Shaofeng Cai, Zhongxiang Dai, Beng Chin Ooi, Bryan Kian Hsiang Low  
    In *The 10th International Conference on Learning Representations* (**ICLR**), 2022  
    Acceptance rate: 32.3%. [[pdf](https://openreview.net/pdf?id=v-v1cpNNK_v)]  
    <details>
        <summary>Abstract</summary>
        Recent years have witnessed a surging interest in Neural Architecture Search (NAS). Various algorithms have been proposed to improve the search efficiency and effectiveness of NAS, i.e., to reduce the search cost and improve the generalization performance of the selected architectures, respectively. However, the search efficiency of these algorithms is severely limited by the need for model training during the search process. To overcome this limitation, we propose a novel NAS algorithm called NAS at Initialization (NASI) that exploits the capability of a Neural Tangent Kernel in being able to characterize the performance of candidate architectures at initialization, hence allowing model training to be completely avoided to boost the search efficiency. Besides the improved search efficiency, NASI also achieves competitive search effectiveness on various datasets like CIFAR-10/100 and ImageNet. Further, NASI is shown to be label- and data-agnostic under mild conditions, which guarantees the transferability of architectures selected by our NASI over different datasets. 
    </details>  


<h4 class="archive__subtitle">{{ "2021" }}</h4>  

- <span style="color: royalblue">Dynamic Routing Networks.</span>  
    Shaofeng Cai, **Yao Shu**, Wei Wang  
    In *Proceedings of the IEEE/CVF Winter Conference on Applications of Computer Vision* (**WACV**), 2021  
    <details>
        <summary>Abstract</summary>
        The deployment of deep neural networks in real-world applications is mostly restricted by their high inference costs. Extensive efforts have been made to improve the accuracy with expert-designed or algorithm-searched architectures. However, the incremental improvement is typically achieved with increasingly more expensive models that only a small portion of input instances really need. Inference with a static architecture that processes all input instances via the same transformation would thus incur unnecessary computational costs. Therefore, customizing the model capacity in an instance-aware manner is much needed for higher inference efficiency. In this paper, we propose Dynamic Routing Networks (DRNets), which support efficient instance-aware inference by routing the input instance to only necessary transformation branches selected from a candidate set of branches for each connection between transformation nodes. The branch selection is dynamically determined via the corresponding branch importance weights, which are first generated from lightweight hypernetworks (RouterNets) and then recalibrated with Gumbel-Softmax before the selection. Extensive experiments show that DRNets can reduce a substantial amount of parameter size and FLOPs during inference with prediction performance comparable to state-of-the-art architectures.
    </details>  


<h4 class="archive__subtitle">{{ "2020" }}</h4>  

- <span style="color: royalblue">Understanding Architectures Learnt by Cell-based Neural Architecture Search.</span>  
    **Yao Shu**, Wei Wang, Shaofeng Cai  
    In *The 8th International Conference on Learning Representations* (**ICLR**), 2020  
    Acceptance rate: 26.5%. [[code](https://github.com/shuyao95/Understanding-NAS.git), [pdf](https://openreview.net/pdf?id=BJxH22EKPS)]  
    <details>
        <summary>Abstract</summary>
        Neural architecture search (NAS) searches architectures automatically for given tasks, e.g., image classification and language modeling. Improving the search efficiency and effectiveness have attracted increasing attention in recent years. However, few efforts have been devoted to understanding the generated architectures. In this paper, we first reveal that existing NAS algorithms (e.g., DARTS, ENAS) tend to favor architectures with wide and shallow cell structures. These favorable architectures consistently achieve fast convergence and are consequently selected by NAS algorithms. Our empirical and theoretical study further confirms that their fast convergence derives from their smooth loss landscape and accurate gradient information. Nonetheless, these architectures may not necessarily lead to better generalization performance compared with other candidate architectures in the same search space, and therefore further improvement is possible by revising existing NAS algorithms.
    </details>  


<h2 class="archive__title">{{ "Preprints" }}</h2>

- <span style="color: royalblue">Tight Lower Complexity Bounds for Strongly Convex Finite-Sum Optimization.</span>  
    Min Zhang, **Yao Shu**, Kun He  
    [arXiv:2010.08766](https://arxiv.org/abs/2010.08766), 2020
    <details>
        <summary>Abstract</summary>
        Finite-sum optimization plays an important role in the area of machine learning, and hence has triggered a surge of interest in recent years. To address this optimization problem, various randomized incremental gradient methods have been proposed with guaranteed upper and lower complexity bounds for their convergence. Nonetheless, these lower bounds rely on certain conditions: deterministic optimization algorithm, or fixed probability distribution for the selection of component functions. Meanwhile, some lower bounds even do not match the upper bounds of the best known methods in certain cases. To break these limitations, we derive tight lower complexity bounds of randomized incremental gradient methods, including SAG, SAGA, SVRG, and SARAH, for two typical cases of finite-sum optimization. Specifically, our results tightly match the upper complexity of Katyusha or VRADA when each component function is strongly convex and smooth, and tightly match the upper complexity of SDCA without duality and of KatyushaX when the finite-sum function is strongly convex and the component functions are average smooth.
    </details>  
- <span style="color: royalblue">Effective and Efficient Dropout for Deep Convolutional Neural Networks.</span>  
    Shaofeng Cai, **Yao Shu**, Wei Wang, Meihui Zhang, Gang Chen, Beng Chin Ooi  
    [arXiv:1904.03392](https://arxiv.org/abs/1904.03392), 2019  
    <details>
        <summary>Abstract</summary>
        Convolutional Neural networks (CNNs) based applications have become ubiquitous, where proper regularization is greatly needed. To prevent large neural network models from overfitting, dropout has been widely used as an efficient regularization technique in practice. However, many recent works show that the standard dropout is ineffective or even detrimental to the training of CNNs. In this paper, we revisit this issue and examine various dropout variants in an attempt to improve existing dropout-based regularization techniques for CNNs. We attribute the failure of standard dropout to the conflict between the stochasticity of dropout and its following Batch Normalization (BN), and propose to reduce the conflict by placing dropout operations right before the convolutional operation instead of BN, or totally address this issue by replacing BN with Group Normalization (GN). We further introduce a structurally more suited dropout variant Drop-Conv2d, which provides more efficient and effective regularization for deep CNNs. These dropout variants can be readily integrated into the building blocks of CNNs and implemented in existing deep learning platforms. Extensive experiments on benchmark datasets including CIFAR, SVHN and ImageNet are conducted to compare the existing building blocks and the proposed ones with dropout training. Results show that our building blocks improve over state-of-the-art CNNs significantly, which is mainly due to the better regularization and implicit model ensemble effect.
    </details>  
- <span style="color: royalblue">Efficient Memory Management for GPU-based Deep Learning Systems.</span>  
    Junzhe Zhang, Sai Ho Yeung, **Yao Shu**, Bingsheng He, Wei Wang  
    [arXiv:1903.06631](https://arxiv.org/abs/1903.06631), 2019  
    <details>
        <summary>Abstract</summary>
        GPU (graphics processing unit) has been used for many data-intensive applications. Among them, deep learning systems are one of the most important consumer systems for GPU nowadays. As deep learning applications impose deeper and larger models in order to achieve higher accuracy, memory management becomes an important research topic for deep learning systems, given that GPU has limited memory size. Many approaches have been proposed towards this issue, e.g., model compression and memory swapping. However, they either degrade the model accuracy or require a lot of manual intervention. In this paper, we propose two orthogonal approaches to reduce the memory cost from the system perspective. Our approaches are transparent to the models, and thus do not affect the model accuracy. They are achieved by exploiting the iterative nature of the training algorithm of deep learning to derive the lifetime and read/write order of all variables. With the lifetime semantics, we are able to implement a memory pool with minimal fragments. However, the optimization problem is NP-complete. We propose a heuristic algorithm that reduces up to 13.3% of memory compared with Nvidia's default memory pool with equal time complexity. With the read/write semantics, the variables that are not in use can be swapped out from GPU to CPU to reduce the memory footprint. We propose multiple swapping strategies to automatically decide which variable to swap and when to swap out (in), which reduces the memory cost by up to 34.2% without communication overhead.
    </details>  


<h2 class="archive__title">{{ "Selected Honors and Awards" }}</h2> 

- Dean's Graduate Research Excellence Award, School of Computing, NUS, 2022 ([the news](https://www.comp.nus.edu.sg/programmes/pg/awards/deans/))
- 2nd prize of 5th AutoML Challenge (AutoML for Temporal Relational Data) in the KDD Cup 2019 provided by 4Paradigm, ChaLearn and Microsoft, June 2019 ([our solution](https://github.com/shuyao95/kddcup2019-automl.git), [the news](https://www.4paradigm.com/competition/kddcup2019))
- Honor of Outstanding Student, 2015
- 2nd prize for The Chinese Mathematics Competitions (Non-professional), 2013

<h2 class="archive__title">{{ "Teaching Activities" }}</h2>

- Teaching assistant for *CS3244 Machine Learning*, School of Computing, NUS (Spring 2021)
- Teaching assistant for *CS5242 Neural Networks and Deep Learning*, School of Computing, NUS (Fall 2019)
- Teaching assistant for *CS5242 Neural Networks and Deep Learning*, School of Computing, NUS (Spring 2019)

<h2 class="archive__title">{{ "Professional Services" }}</h2>
- Invited to serve as a reviewer for ICML, NeurIPS, ACML, ICLR, AAMAS, AISTATS, 2022
- Invited to serve as a reviewer for ICML, UAI, 2023

<h2 class="archive__title">{{ "Main Collaborators" }}</h2>
- [Arun Verma](https://arunv3rma.github.io), Research Fellow, School of Computing, NUS
- [Cai Shaofeng](https://solopku.github.io), Research Fellow, School of Computing, NUS
- [Dai Zhongxiang](https://daizhongxiang.github.io), Research Fellow, School of Computing, NUS
- [Flint Xiaofeng Fan](https://flint-xf-fan.github.io), Ph.D., School of Computing, NUS
- [Wu Zhaoxuan](https://zhaoxuanwu.github.io), Ph.D., Institute of Data Science, NUS