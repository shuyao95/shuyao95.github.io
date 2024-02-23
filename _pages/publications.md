---
title:  "PUBLICATIONS"
layout: single
permalink: /publications/
author_profile: true
comments: false
toc: true
toc_sticky: true
---

<!-- ## Accepted Papers -->
\# denotes corresponding author, * denotes equal contribution. 

## Generative Models
- <span style="color: royalblue">Use Your INSTINCT: INSTruction optimization usIng Neural bandits Coupled with Transformers.</span>  
    Xiaoqiang Lin\*, Zhaoxuan Wu\*, Zhongxiang Dai, Wenyang Hu, **Yao Shu**, See-Kiong Ng, Patrick Jaillet and Kian Hsiang Low  
    [arXiv:2310.02905](https://arxiv.org/abs/2310.02905), 2023
    <details>
        <summary>Abstract</summary>
        Large language models (LLMs) have shown remarkable instruction-following capabilities and achieved impressive performances in various applications. However, the performances of LLMs depend heavily on the instructions given to them, which are typically manually tuned with substantial human efforts. Recent work has used the query-efficient Bayesian optimization (BO) algorithm to automatically optimize the instructions given to black-box LLMs. However, BO usually falls short when optimizing highly sophisticated (e.g., high-dimensional) objective functions, such as the functions mapping an instruction to the performance of an LLM. This is mainly due to the limited expressive power of the Gaussian process (GP) model which is used by BO as a surrogate to model the objective function. Meanwhile, it has been repeatedly shown that neural networks (NNs), especially pre-trained transformers, possess strong expressive power and can model highly complex functions. So, we adopt a neural bandit algorithm which replaces the GP in BO by an NN surrogate to optimize instructions for black-box LLMs. More importantly, the neural bandit algorithm allows us to naturally couple the NN surrogate with the hidden representation learned by a pre-trained transformer (i.e., an open-source LLM), which significantly boosts its performance. These motivate us to propose our INSTruction optimization usIng Neural bandits Coupled with Transformers} (INSTINCT) algorithm. We perform instruction optimization for ChatGPT and use extensive experiments to show that our INSTINCT consistently outperforms the existing methods in different tasks, such as in various instruction induction tasks and the task of improving the zero-shot chain-of-thought instruction.
    </details>  

## Optimization & Decision-Making
- <span style="color: royalblue">OptEx: Expediting First-Order Optimization with Approximately Parallelized Iterations.</span>  
    **Yao Shu**, Jiongfeng Fang, Ying Tiffany He, Fei Richard Yu  
    [arXiv:2402.11427](https://arxiv.org/abs/2402.11427), 2024
    <details>
        <summary>Abstract</summary>
        Federated optimization, an emerging paradigm which finds wide real-world applications such as federated learning, enables multiple clients (e.g., edge devices) to collaboratively optimize a global function. The clients do not share their local datasets and typically only share their local gradients. However, the gradient information is not available in many applications of federated optimization, which hence gives rise to the paradigm of federated zeroth-order optimization (ZOO). Existing federated ZOO algorithms suffer from the limitations of query and communication inefficiency, which can be attributed to (a) their reliance on a substantial number of function queries for gradient estimation and (b) the significant disparity between their realized local updates and the intended global updates. To this end, we (a) introduce trajectory-informed gradient surrogates which is able to use the history of function queries during optimization for accurate and query-efficient gradient estimation, and (b) develop the technique of adaptive gradient correction using these gradient surrogates to mitigate the aforementioned disparity. Based on these, we propose the federated zeroth-order optimization using trajectory-informed surrogate gradients (FZooS) algorithm for query- and communication-efficient federated ZOO. Our FZooS achieves theoretical improvements over the existing approaches, which is supported by our real-world experiments such as federated black-box adversarial attack and federated non-differentiable metric optimization.
    </details>  
- <span style="color: royalblue">Federated Zeroth-Order Optimization using Trajectory-Informed Surrogate Gradients.</span>  
    **Yao Shu**, Xiaoqiang Lin, Zhongxiang Dai, Bryan Kian Hsiang Low  
    [arXiv:2308.04077](https://arxiv.org/abs/2308.04077), 2023
    <details>
        <summary>Abstract</summary>
        Federated optimization, an emerging paradigm which finds wide real-world applications such as federated learning, enables multiple clients (e.g., edge devices) to collaboratively optimize a global function. The clients do not share their local datasets and typically only share their local gradients. However, the gradient information is not available in many applications of federated optimization, which hence gives rise to the paradigm of federated zeroth-order optimization (ZOO). Existing federated ZOO algorithms suffer from the limitations of query and communication inefficiency, which can be attributed to (a) their reliance on a substantial number of function queries for gradient estimation and (b) the significant disparity between their realized local updates and the intended global updates. To this end, we (a) introduce trajectory-informed gradient surrogates which is able to use the history of function queries during optimization for accurate and query-efficient gradient estimation, and (b) develop the technique of adaptive gradient correction using these gradient surrogates to mitigate the aforementioned disparity. Based on these, we propose the federated zeroth-order optimization using trajectory-informed surrogate gradients (FZooS) algorithm for query- and communication-efficient federated ZOO. Our FZooS achieves theoretical improvements over the existing approaches, which is supported by our real-world experiments such as federated black-box adversarial attack and federated non-differentiable metric optimization.
    </details>  
- <span style="color: royalblue">Quantum Bayesian Optimization.</span>  
    Zhongxiang Dai\*, Gregory Kang Ruey Lau\*, Arun Verma, **Yao Shu**, Kian Hsiang Low and Patrick Jaillet  
    In *The 37th Conference on Neural Information Processing Systems* (**NeurIPS**), 2023  
    Acceptance rate: 26.1%. [[pdf](https://openreview.net/pdf?id=Y44NurSDjq)]  
    <details>
        <summary>Abstract</summary>
        Kernelized bandits, also known as Bayesian optimization (BO), has been a prevalent method for optimizing complicated black-box reward functions. Various BO algorithms have been theoretically shown to enjoy upper bounds on their cumulative regret which are sub-linear in the number $T$ of iterations, and a regret lower bound of $\Omega(\sqrt{T})$ has been derived which represents the unavoidable regrets for any classical BO algorithm. Recent works on quantum bandits have shown that with the aid of quantum computing, it is possible to achieve tighter regret upper bounds better than their corresponding classical lower bounds. However, these works are restricted to either multi-armed or linear bandits, and are hence not able to solve sophisticated real-world problems with non-linear reward functions. To this end, we introduce the quantum-Gaussian process-upper confidence bound (Q-GP-UCB) algorithm. To the best of our knowledge, our Q-GP-UCB is the first BO algorithm able to achieve a regret upper bound of $O(\text{ploy}\log T)$, which is significantly smaller than its regret lower bound of $\Omega(\sqrt{T})$ in the classical setting. Moreover, thanks to our novel analysis of the confidence ellipsoid, our Q-GP-UCB with the linear kernel achieves a smaller regret than the quantum linear UCB algorithm from the previous work. We use simulations to verify that the theoretical quantum speedup achieved by our Q-GP-UCB is also potentially relevant in practice.
    </details> 
- <span style="color: royalblue">Exploiting Correlated Auxiliary Feedback in Parameterized Bandits.</span>  
    Arun Verma, Zhongxiang Dai, **Yao Shu** and Kian Hsiang Low  
    In *The 37th Conference on Neural Information Processing Systems* (**NeurIPS**), 2023  
    Acceptance rate: 26.1%. [[pdf](https://openreview.net/pdf?id=vM5VnNQ4n7)]  
    <details>
        <summary>Abstract</summary>
        We study a novel variant of the parameterized bandits problem in which the learner can observe auxiliary feedback that is correlated with the observed reward. The auxiliary feedback is readily available in many real-life applications, e.g., an online platform that wants to recommend the best-rated services to its users can observe the user's rating of service (rewards) and collect additional information like service delivery time (auxiliary feedback). We first develop a method that exploits auxiliary feedback to build a reward estimator with tight confidence bounds, leading to a smaller regret. We then characterize the regret reduction in terms of the correlation coefficient between reward and auxiliary feedback. Experimental results in different settings also verify the performance gain achieved by our proposed method.
    </details> 
- <span style="color: royalblue">Zeroth-Order Optimization with Trajectory-Informed Derivative Estimation.</span>  
    **Yao Shu**\*, Zhongxiang Dai\*, Weicong Sng, Arun Verma, Patrick Jaillet and Bryan Kian Hsiang Low  
    In *The 11th International Conference on Learning Representations* (**ICLR**), 2023  
    Acceptance rate: 31.8%. [[pdf](https://openreview.net/pdf?id=n1bLgxHW6jW)]  
    <details>
        <summary>Abstract</summary>
        Zeroth-order (ZO) optimization, in which the derivative is unavailable, has recently succeeded in many important machine learning applications. Existing algorithms rely on finite difference (FD) methods for derivative estimation and gradient descent (GD)-based approaches for optimization. However, these algorithms suffer from query inefficiency because additional function queries are required for derivative estimation in their every GD update, which typically hinders their deployment in applications where every function query is expensive. To this end, we propose a trajectory-informed derivative estimation method which only uses the optimization trajectory (i.e., the history of function queries during optimization) and hence eliminates the need for additional function queries to estimate a derivative. Moreover, based on our derivative estimation, we propose the technique of dynamic virtual updates, which allows us to reliably perform multiple steps of GD updates without reapplying derivative estimation. Based on these two contributions, we introduce the zeroth-order optimization with trajectory-informed derivative estimation (ZoRD) algorithm for query-efficient ZO optimization. We theoretically demonstrate that our trajectory-informed derivative estimation and our ZoRD algorithm improve over existing approaches, which is then supported by our real-world experiments such as black-box adversarial attack, non-differentiable metric optimization and derivative-free reinforcement learning.
    </details>  
- <span style="color: royalblue">Federated Neural Bandit.</span>  
    Zhongxiang Dai, **Yao Shu*#, Arun Verma, Flint Xiaofeng Fan, Bryan Kian Hsiang Low and Patrick Jaillet  
    In *The 11th International Conference on Learning Representations* (**ICLR**), 2023  
    Acceptance rate: 31.8%. [[pdf](https://openreview.net/pdf?id=38m4h8HcNRL)]  
    <details>
        <summary>Abstract</summary>
        Recent works on neural contextual bandits have achieved compelling performances due to their ability to leverage the strong representation power of neural networks (NNs) for reward prediction. Many applications of contextual bandits involve multiple agents who collaborate without sharing raw observations, thus giving rise to the setting of federated contextual bandits}. Existing works on federated contextual bandits rely on linear or kernelized bandits, which may fall short when modeling complex real-world reward functions. So, this paper introduces the federated neural-upper confidence bound (FN-UCB) algorithm. To better exploit the federated setting, FN-UCB adopts a weighted combination of two UCBs: UCB^a allows every agent to additionally use the observations from the other agents to accelerate exploration (without sharing raw observations), while UCB^b uses an NN with aggregated parameters for reward prediction in a similar way to federated averaging for supervised learning. Notably, the weight between the two UCBs required by our theoretical analysis is amenable to an interesting interpretation, which emphasizes UCB^a initially for accelerated exploration and relies more on UCB^b later after enough observations have been collected to train the NNs for accurate reward prediction (i.e., reliable exploitation). We prove sub-linear upper bounds on both the cumulative regret and the number of communication rounds of FN-UCB, and empirically demonstrate its competitive performance.
    </details>  
- <span style="color: royalblue">Sample-Then-Optimize Batch Neural Thompson Sampling.</span>  
    Zhongxiang Dai, **Yao Shu**#, Bryan Kian Hsiang Low, Patrick Jaillet  
    In *The 36th Conference on Neural Information Processing Systems* (**NeurIPS**), 2022  
    Acceptance rate: 25.6%. [[pdf](https://arxiv.org/pdf/2210.06850.pdf)]  
    <details>
        <summary>Abstract</summary>
        Bayesian optimization (BO), which uses a Gaussian process (GP) as a surrogate to model its objective function, is popular for black-box optimization. However, due to the limitations of GPs, BO underperforms in some problems such as those with categorical, high-dimensional or image inputs. To this end, recent works have used the highly expressive neural networks (NNs) as the surrogate model and derived theoretical guarantees using the theory of neural tangent kernel (NTK). However, these works suffer from the limitations of the requirement to invert an extremely large parameter matrix and the restriction to the sequential (rather than batch) setting. To overcome these limitations, we introduce two algorithms based on the Thompson sampling (TS) policy named Sample-Then-Optimize Batch Neural TS (STO-BNTS) and STO-BNTS-Linear. To choose an input query, we only need to train an NN (resp. a linear model) and then choose the query by maximizing the trained NN (resp. linear model), which is equivalently sampled from the GP posterior with the NTK as the kernel function. As a result, our algorithms sidestep the need to invert the large parameter matrix yet still preserve the validity of the TS policy. Next, we derive regret upper bounds for our algorithms with batch evaluations, and use insights from batch BO and NTK to show that they are asymptotically no-regret under certain conditions. Finally, we verify their empirical effectiveness using practical AutoML and reinforcement learning experiments. 
    </details>  
- <span style="color: royalblue">Tight Lower Complexity Bounds for Strongly Convex Finite-Sum Optimization.</span>  
    Min Zhang, **Yao Shu**, Kun He  
    [arXiv:2010.08766](https://arxiv.org/abs/2010.08766), 2020
    <details>
        <summary>Abstract</summary>
        Finite-sum optimization plays an important role in the area of machine learning, and hence has triggered a surge of interest in recent years. To address this optimization problem, various randomized incremental gradient methods have been proposed with guaranteed upper and lower complexity bounds for their convergence. Nonetheless, these lower bounds rely on certain conditions: deterministic optimization algorithm, or fixed probability distribution for the selection of component functions. Meanwhile, some lower bounds even do not match the upper bounds of the best known methods in certain cases. To break these limitations, we derive tight lower complexity bounds of randomized incremental gradient methods, including SAG, SAGA, SVRG, and SARAH, for two typical cases of finite-sum optimization. Specifically, our results tightly match the upper complexity of Katyusha or VRADA when each component function is strongly convex and smooth, and tightly match the upper complexity of SDCA without duality and of KatyushaX when the finite-sum function is strongly convex and the component functions are average smooth.
    </details>  

## Data-Centric AI
- <span style="color: royalblue">DAVINZ: Data Valuation using Deep Neural Networks at Initialization.</span>  
    Zhaoxuan Wu, **Yao Shu**, Bryan Kian Hsiang Low  
    In *The 39th International Conference on Machine Learning* (**ICML**), 2022  
    Acceptance rate: 21.9%. [[pdf](https://proceedings.mlr.press/v162/wu22j/wu22j.pdf)] 
    <details>
        <summary>Abstract</summary>
        Recent years have witnessed a surge of interest in developing trustworthy methods to evaluate the value of data in many real-world applications, e.g., collaborative machine learning, data marketplaces, etc. Existing data valuation methods typically valuate data using the generalization performance of converged machine learning models after their long-term model training, making data valuation on large complex deep neural networks (DNNs) unaffordable. To this end, we theoretically derive a domain-aware generalization bound to estimate the generalization performance of DNNs without model training. We then exploit this theoretically derived generalization bound to develop a novel training-free data valuation method named data valuation at initialization (DAVINZ) on DNNs, which consistently achieves remarkable effectiveness and efficiency in practice. Moreover, our training-free DAVINZ, surprisingly, can even theoretically and empirically enjoy the desirable properties that training-based data valuation methods usually attain, making it more trustworthy in practice. 
    </details>  

## Neural Architecture Search
- <span style="color: royalblue">Robustifying and Boosting Training-Free Neural Architecture Search.</span>  
    Zhenfeng He, **Yao Shu**#, Zhongxiang Dai, Bryan Kian Hsiang Low  
    In *The 12th International Conference on Learning Representations* (**ICLR**), 2024  
    Acceptance rate: 31%. [[pdf](https://openreview.net/pdf?id=qPloNoDJZn)]  
    <details>
        <summary>Abstract</summary>
        Neural architecture search (NAS) has become a key component of AutoML and a standard tool to automate the design of deep neural networks. Recently, training-free NAS as an emerging paradigm has successfully reduced the search costs of standard training-based NAS by estimating the true architecture performance with only training-free metrics. Nevertheless, the estimation ability of these metrics typically varies across different tasks, making it challenging to achieve robust and consistently good search performance on diverse tasks with only a single training-free metric. Meanwhile, the estimation gap between training-free metrics and the true architecture performances limits training-free NAS to achieve superior performance. To address these challenges, we propose the robustifying and boosting training-free NAS (RoBoT) algorithm which (a) employs the optimized combination of existing training-free metrics explored from Bayesian optimization to develop a robust and consistently better-performing metric on diverse tasks, and (b) applies greedy search, i.e., the exploitation, on the newly developed metric to bridge the aforementioned gap and consequently to boost the search performance of standard training-free NAS further. Remarkably, the expected performance of our RoBoT can be theoretically guaranteed, which improves over the existing training-free NAS under mild conditions with additional interesting insights. Our extensive experiments on various NAS benchmark tasks yield substantial empirical evidence to support our theoretical results.
    </details>  
- <span style="color: royalblue">Unifying and Boosting Gradient-Based Training-Free Neural Architecture Search.</span>  
    **Yao Shu**, Zhongxiang Dai, Zhaoxuan Wu, Bryan Kian Hsiang Low  
    In *The 36th Conference on Neural Information Processing Systems* (**NeurIPS**), 2022  
    Acceptance rate: 25.6%. [[pdf](https://arxiv.org/pdf/2201.09785.pdf)]  
    <details>
        <summary>Abstract</summary>
        Neural architecture search (NAS) has gained immense popularity owing to its ability to automate neural architecture design. A number of training-free metrics are recently proposed to realize NAS without training, hence making NAS more scalable. Despite their competitive empirical performances, a unified theoretical understanding of these training-free metrics is lacking. As a consequence, (a) the relationships among these metrics are unclear, (b) there is no theoretical interpretation for their empirical performances, and (c) there may exist untapped potential in existing training-free NAS, which probably can be unveiled through a unified theoretical understanding. To this end, this paper presents a unified theoretical analysis of gradient-based training-free NAS, which allows us to (a) theoretically study their relationships, (b) theoretically guarantee their generalization performances, and (c) exploit our unified theoretical understanding to develop a novel framework named hybrid NAS (HNAS) which consistently boosts training-free NAS in a principled way. Remarkably, HNAS can enjoy the advantages of both training-free (i.e., superior search efficiency) and training-based (i.e., remarkable search effectiveness) NAS, which we have demonstrated through extensive experiments.
    </details>  
- <span style="color: royalblue">Neural Ensemble Search via Bayesian Sampling.</span>  
    **Yao Shu**, Yizhou Chen, Zhongxiang Dai, Bryan Kian Hsiang Low  
    In *The 38th Conference on Uncertainty in Artificial Intelligence* (**UAI**), 2022  
    Acceptance rate: 32.3%. [[pdf](https://openreview.net/pdf?id=Bh4lBPUjqg9)]  
    <details>
        <summary>Abstract</summary>
        Recently, neural architecture search (NAS) has been applied to automate the design of neural networks in real-world applications. A large number of algorithms have been developed to improve the search cost or the performance of the final selected architectures in NAS. Unfortunately, these NAS algorithms aim to select only one single well-performing architecture from their search spaces and thus have overlooked the capability of neural network ensemble (i.e., an ensemble of neural networks with diverse architectures) in achieving improved performance over a single final selected architecture. To this end, we introduce a novel neural ensemble search algorithm, called neural ensemble search via Bayesian sampling (NESBS), to effectively and efficiently select well-performing neural network ensembles from a NAS search space. In our extensive experiments, NESBS algorithm is shown to be able to achieve improved performance over state-of-the-art NAS algorithms while incurring a comparable search cost, indicating the superior of our NESBS algorithm over these conventional NAS algorithms in practice. 
    </details>  
- <span style="color: royalblue">NASI: Label- and Data-agnostic Neural Architecture Search at Initialization.</span>  
    **Yao Shu**, Shaofeng Cai, Zhongxiang Dai, Beng Chin Ooi, Bryan Kian Hsiang Low  
    In *The 10th International Conference on Learning Representations* (**ICLR**), 2022  
    Acceptance rate: 32.3%. [[pdf](https://openreview.net/pdf?id=v-v1cpNNK_v)]  
    <details>
        <summary>Abstract</summary>
        Recent years have witnessed a surging interest in Neural Architecture Search (NAS). Various algorithms have been proposed to improve the search efficiency and effectiveness of NAS, i.e., to reduce the search cost and improve the generalization performance of the selected architectures, respectively. However, the search efficiency of these algorithms is severely limited by the need for model training during the search process. To overcome this limitation, we propose a novel NAS algorithm called NAS at Initialization (NASI) that exploits the capability of a Neural Tangent Kernel in being able to characterize the performance of candidate architectures at initialization, hence allowing model training to be completely avoided to boost the search efficiency. Besides the improved search efficiency, NASI also achieves competitive search effectiveness on various datasets like CIFAR-10/100 and ImageNet. Further, NASI is shown to be label- and data-agnostic under mild conditions, which guarantees the transferability of architectures selected by our NASI over different datasets. 
    </details>  
- <span style="color: royalblue">Understanding Architectures Learnt by Cell-based Neural Architecture Search.</span>  
    **Yao Shu**, Wei Wang, Shaofeng Cai  
    In *The 8th International Conference on Learning Representations* (**ICLR**), 2020  
    Acceptance rate: 26.5%. [[code](https://github.com/shuyao95/Understanding-NAS.git), [pdf](https://openreview.net/pdf?id=BJxH22EKPS)]  
    <details>
        <summary>Abstract</summary>
        Neural architecture search (NAS) searches architectures automatically for given tasks, e.g., image classification and language modeling. Improving the search efficiency and effectiveness have attracted increasing attention in recent years. However, few efforts have been devoted to understanding the generated architectures. In this paper, we first reveal that existing NAS algorithms (e.g., DARTS, ENAS) tend to favor architectures with wide and shallow cell structures. These favorable architectures consistently achieve fast convergence and are consequently selected by NAS algorithms. Our empirical and theoretical study further confirms that their fast convergence derives from their smooth loss landscape and accurate gradient information. Nonetheless, these architectures may not necessarily lead to better generalization performance compared with other candidate architectures in the same search space, and therefore further improvement is possible by revising existing NAS algorithms.
    </details>  

## Others
- <span style="color: royalblue">Dynamic Routing Networks.</span>  
    Shaofeng Cai, **Yao Shu**, Wei Wang  
    In *Proceedings of the IEEE/CVF Winter Conference on Applications of Computer Vision* (**WACV**), 2021  
    <details>
        <summary>Abstract</summary>
        The deployment of deep neural networks in real-world applications is mostly restricted by their high inference costs. Extensive efforts have been made to improve the accuracy with expert-designed or algorithm-searched architectures. However, the incremental improvement is typically achieved with increasingly more expensive models that only a small portion of input instances really need. Inference with a static architecture that processes all input instances via the same transformation would thus incur unnecessary computational costs. Therefore, customizing the model capacity in an instance-aware manner is much needed for higher inference efficiency. In this paper, we propose Dynamic Routing Networks (DRNets), which support efficient instance-aware inference by routing the input instance to only necessary transformation branches selected from a candidate set of branches for each connection between transformation nodes. The branch selection is dynamically determined via the corresponding branch importance weights, which are first generated from lightweight hypernetworks (RouterNets) and then recalibrated with Gumbel-Softmax before the selection. Extensive experiments show that DRNets can reduce a substantial amount of parameter size and FLOPs during inference with prediction performance comparable to state-of-the-art architectures.
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

<!-- 
## Main Collaborators
- [Arun Verma](https://arunv3rma.github.io), Research Fellow, School of Computing, NUS
- [Cai Shaofeng](https://solopku.github.io), Research Fellow, School of Computing, NUS
- [Dai Zhongxiang](https://daizhongxiang.github.io), Research Fellow, School of Computing, NUS
- [Wu Zhaoxuan](https://zhaoxuanwu.github.io), Ph.D., Institute of Data Science, NUS -->