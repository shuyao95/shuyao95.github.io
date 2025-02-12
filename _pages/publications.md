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

## Learning for Optimization
*To make optimization more efficient and effective!*

### Kernelized Optimization
- <span style="color: royalblue">OptEx: Expediting First-Order Optimization with Approximately Parallelized Iterations.</span>  
    **Yao Shu**, Jiongfeng Fang, Ying Tiffany He, Fei Richard Yu  
    <span style="color: Red">Key Words: First-Order Optimization, Parallelization</span>   
    In <span style="color: MediumSeaGreen">*The 38th Conference on Neural Information Processing Systems* (**NeurIPS**)</span>, 2024   
    [[arXiv](https://arxiv.org/abs/2402.11427), [pdf](https://openreview.net/pdf?id=MzNjnbgcPN)]  
    <details>
        <summary>Abstract</summary>
        First-order optimization (FOO) algorithms are pivotal in numerous computational domains such as machine learning and signal denoising. However, their application to complex tasks like neural network training often entails significant inefficiencies due to the need for many sequential iterations for convergence. In response, we introduce first-order optimization expedited with approximately parallelized iterations (OptEx), the first framework that enhances the efficiency of FOO by leveraging parallel computing to mitigate its iterative bottleneck. OptEx employs kernelized gradient estimation to make use of gradient history for future gradient prediction, enabling parallelization of iterations -- a strategy once considered impractical because of the inherent iterative dependency in FOO. We provide theoretical guarantees for the reliability of our kernelized gradient estimation and the iteration complexity of SGD-based OptEx, confirming that estimation errors diminish to zero as historical gradients accumulate and that SGD-based OptEx enjoys an effective acceleration rate of $\Theta(\sqrt{N})$ over standard SGD given parallelism of N. We also use extensive empirical studies, including synthetic functions, reinforcement learning tasks, and neural network training across various datasets, to underscore the substantial efficiency improvements achieved by OptEx.
    </details>  
- <span style="color: royalblue">Heterogeneous Federated Zeroth-Order Optimization using Gradient Surrogates.</span>  
    **Yao Shu**, Xiaoqiang Lin, Zhongxiang Dai, Bryan Kian Hsiang Low  
    <span style="color: Red">Key Words: Zeroth-Order Optimization, Federated Optimization, Heterogeneity</span>  
    In <span style="color: MediumSeaGreen">*Differentiable Almost Everything Workshop* @ **ICML**</span>, 2024  
    [[arXiv](https://arxiv.org/abs/2308.04077), [pdf](https://openreview.net/pdf?id=8E2YX0vf05), [code](https://github.com/shuyao95/FZooS)]  
    <details>
        <summary>Abstract</summary>
        Federated optimization, an emerging paradigm that finds wide applications, e.g., federated learning, enables multiple clients (e.g., edge devices) to collaboratively optimize a global function by sharing their local gradients. However, the gradient information is not available in many applications, giving rise to the paradigm of federated zeroth-order optimization (ZOO). Existing federated ZOO algorithms typically suffer from the limitations of query and communication round inefficiency, which can be attributed to (a) their reliance on a substantial number of function queries for gradient estimation and (b) the significant disparity between their realized local updates and the intended global updates caused by client heterogeneity. To this end, we (a) introduce trajectory-informed gradient surrogates which are capable of using the history of function queries during optimization for accurate and query-efficient gradient estimation, and (b) develop the technique of adaptive gradient correction using these surrogates to mitigate the aforementioned disparity. With these, we propose the federated zeroth-order optimization using gradient surrogates (FZooS) algorithm for query- and communication round-efficient heterogeneous federated ZOO, which is supported by our theoretical analyses and extensive experiments.
    </details>  
- <span style="color: royalblue">Zeroth-Order Optimization with Trajectory-Informed Derivative Estimation.</span>  
    **Yao Shu**\*, Zhongxiang Dai\*, Weicong Sng, Arun Verma, Patrick Jaillet and Bryan Kian Hsiang Low  
    <span style="color: Red">Key Words: Zeroth-Order Optimization, Derived Gaussian Process</span>  
    In <span style="color: MediumSeaGreen">*The 11th International Conference on Learning Representations* (**ICLR**)</span>, 2023  
    <!-- Acceptance rate: 31.8%  -->
    [[pdf](https://openreview.net/pdf?id=n1bLgxHW6jW), [code](https://github.com/shuyao95/ZoRD)]  
    <details>
        <summary>Abstract</summary>
        Zeroth-order (ZO) optimization, in which the derivative is unavailable, has recently succeeded in many important machine learning applications. Existing algorithms rely on finite difference (FD) methods for derivative estimation and gradient descent (GD)-based approaches for optimization. However, these algorithms suffer from query inefficiency because additional function queries are required for derivative estimation in their every GD update, which typically hinders their deployment in applications where every function query is expensive. To this end, we propose a trajectory-informed derivative estimation method which only uses the optimization trajectory (i.e., the history of function queries during optimization) and hence eliminates the need for additional function queries to estimate a derivative. Moreover, based on our derivative estimation, we propose the technique of dynamic virtual updates, which allows us to reliably perform multiple steps of GD updates without reapplying derivative estimation. Based on these two contributions, we introduce the zeroth-order optimization with trajectory-informed derivative estimation (ZoRD) algorithm for query-efficient ZO optimization. We theoretically demonstrate that our trajectory-informed derivative estimation and our ZoRD algorithm improve over existing approaches, which is then supported by our real-world experiments such as black-box adversarial attack, non-differentiable metric optimization and derivative-free reinforcement learning.
    </details>  

### Neuralized Optimization
- <span style="color: royalblue">Federated Neural Bandit.</span>  
    Zhongxiang Dai, **Yao Shu**#, Arun Verma, Flint Xiaofeng Fan, Bryan Kian Hsiang Low and Patrick Jaillet  
    <span style="color: Red">Key Words: Neural Bandit, Neural Tangent Kernel</span>  
    In <span style="color: MediumSeaGreen">*The 11th International Conference on Learning Representations* (**ICLR**)</span>, 2023  
    <!-- Acceptance rate: 31.8%  -->
    [[arXiv](https://arxiv.org/abs/2205.14309), [pdf](https://openreview.net/pdf?id=38m4h8HcNRL), [code](https://github.com/daizhongxiang/Federated-Neural-Bandits)]  
    <details>
        <summary>Abstract</summary>
        Recent works on neural contextual bandits have achieved compelling performances due to their ability to leverage the strong representation power of neural networks (NNs) for reward prediction. Many applications of contextual bandits involve multiple agents who collaborate without sharing raw observations, thus giving rise to the setting of federated contextual bandits. Existing works on federated contextual bandits rely on linear or kernelized bandits, which may fall short when modeling complex real-world reward functions. So, this paper introduces the federated neural-upper confidence bound (FN-UCB) algorithm. To better exploit the federated setting, FN-UCB adopts a weighted combination of two UCBs: UCB^a allows every agent to additionally use the observations from the other agents to accelerate exploration (without sharing raw observations), while UCB^b uses an NN with aggregated parameters for reward prediction in a similar way to federated averaging for supervised learning. Notably, the weight between the two UCBs required by our theoretical analysis is amenable to an interesting interpretation, which emphasizes UCB^a initially for accelerated exploration and relies more on UCB^b later after enough observations have been collected to train the NNs for accurate reward prediction (i.e., reliable exploitation). We prove sub-linear upper bounds on both the cumulative regret and the number of communication rounds of FN-UCB, and empirically demonstrate its competitive performance.
    </details>  
- <span style="color: royalblue">Sample-Then-Optimize Batch Neural Thompson Sampling.</span>  
    Zhongxiang Dai, **Yao Shu**#, Bryan Kian Hsiang Low, Patrick Jaillet  
    <span style="color: Red">Key Words: Bayesian Optimization, Neural Tangent Kernel</span>  
    In <span style="color: MediumSeaGreen">*The 36th Conference on Neural Information Processing Systems* (**NeurIPS**)</span>, 2022  
    <!-- Acceptance rate: 25.6%  -->
    [[arXiv](https://arxiv.org/abs/2210.06850), [pdf](https://arxiv.org/pdf/2210.06850.pdf), [code](https://github.com/daizhongxiang/sto-bnts)]  
    <details>
        <summary>Abstract</summary>
        Bayesian optimization (BO), which uses a Gaussian process (GP) as a surrogate to model its objective function, is popular for black-box optimization. However, due to the limitations of GPs, BO underperforms in some problems such as those with categorical, high-dimensional or image inputs. To this end, recent works have used the highly expressive neural networks (NNs) as the surrogate model and derived theoretical guarantees using the theory of neural tangent kernel (NTK). However, these works suffer from the limitations of the requirement to invert an extremely large parameter matrix and the restriction to the sequential (rather than batch) setting. To overcome these limitations, we introduce two algorithms based on the Thompson sampling (TS) policy named Sample-Then-Optimize Batch Neural TS (STO-BNTS) and STO-BNTS-Linear. To choose an input query, we only need to train an NN (resp. a linear model) and then choose the query by maximizing the trained NN (resp. linear model), which is equivalently sampled from the GP posterior with the NTK as the kernel function. As a result, our algorithms sidestep the need to invert the large parameter matrix yet still preserve the validity of the TS policy. Next, we derive regret upper bounds for our algorithms with batch evaluations, and use insights from batch BO and NTK to show that they are asymptotically no-regret under certain conditions. Finally, we verify their empirical effectiveness using practical AutoML and reinforcement learning experiments. 
    </details>  

### Others
- <span style="color: royalblue">Quantum Bayesian Optimization.</span>  
    Zhongxiang Dai\*, Gregory Kang Ruey Lau\*, Arun Verma, **Yao Shu**, Kian Hsiang Low and Patrick Jaillet  
    <span style="color: Red">Key Words: Bayesian Optimization</span>  
    In <span style="color: MediumSeaGreen">*The 37th Conference on Neural Information Processing Systems* (**NeurIPS**)</span>, 2023  
    <!-- Acceptance rate: 26.1%  -->
    [[arXiv](https://arxiv.org/abs/2310.05373), [pdf](https://openreview.net/pdf?id=Y44NurSDjq), [code](https://github.com/daizhongxiang/Quantum_Bayesian_Optimization)]  
    <details>
        <summary>Abstract</summary>
        Kernelized bandits, also known as Bayesian optimization (BO), has been a prevalent method for optimizing complicated black-box reward functions. Various BO algorithms have been theoretically shown to enjoy upper bounds on their cumulative regret which are sub-linear in the number $T$ of iterations, and a regret lower bound of $\Omega(\sqrt{T})$ has been derived which represents the unavoidable regrets for any classical BO algorithm. Recent works on quantum bandits have shown that with the aid of quantum computing, it is possible to achieve tighter regret upper bounds better than their corresponding classical lower bounds. However, these works are restricted to either multi-armed or linear bandits, and are hence not able to solve sophisticated real-world problems with non-linear reward functions. To this end, we introduce the quantum-Gaussian process-upper confidence bound (Q-GP-UCB) algorithm. To the best of our knowledge, our Q-GP-UCB is the first BO algorithm able to achieve a regret upper bound of $O(\text{ploy}\log T)$, which is significantly smaller than its regret lower bound of $\Omega(\sqrt{T})$ in the classical setting. Moreover, thanks to our novel analysis of the confidence ellipsoid, our Q-GP-UCB with the linear kernel achieves a smaller regret than the quantum linear UCB algorithm from the previous work. We use simulations to verify that the theoretical quantum speedup achieved by our Q-GP-UCB is also potentially relevant in practice.
    </details> 
- <span style="color: royalblue">Exploiting Correlated Auxiliary Feedback in Parameterized Bandits.</span>  
    Arun Verma, Zhongxiang Dai, **Yao Shu** and Kian Hsiang Low  
    <span style="color: Red">Key Words: Parameterized Bandit</span>  
    In <span style="color: MediumSeaGreen">*The 37th Conference on Neural Information Processing Systems* (**NeurIPS**)</span>, 2023  
    <!-- Acceptance rate: 26.1%  -->
    [[arXiv](https://arxiv.org/abs/2311.02715), [pdf](https://openreview.net/pdf?id=vM5VnNQ4n7)]  
    <details>
        <summary>Abstract</summary>
        We study a novel variant of the parameterized bandits problem in which the learner can observe auxiliary feedback that is correlated with the observed reward. The auxiliary feedback is readily available in many real-life applications, e.g., an online platform that wants to recommend the best-rated services to its users can observe the user's rating of service (rewards) and collect additional information like service delivery time (auxiliary feedback). We first develop a method that exploits auxiliary feedback to build a reward estimator with tight confidence bounds, leading to a smaller regret. We then characterize the regret reduction in terms of the correlation coefficient between reward and auxiliary feedback. Experimental results in different settings also verify the performance gain achieved by our proposed method.
    </details> 

## Optimization for Learning  
*To make learning more efficient, effective and easier to deploy!*

### Data-Centric
- <span style="color: royalblue">Localized Zeroth-Order Prompt Optimization.</span>  
    Wenyang Hu\*, **Yao Shu**\*, Zongmin Yu, Zhaoxuan Wu, Xiangqiang Lin, Zhongxiang Dai, See-Kiong Ng, Bryan Kian Hsiang Low  
    <span style="color: Red">Key Words: Prompt Optimization, Zeroth-Order Optimization, Neural Tangent Kernel, Large Language Models</span>  
    In <span style="color: MediumSeaGreen">*In-Context Learning Workshop* @ **ICML**</span>, 2024  
    In <span style="color: MediumSeaGreen">*The 38th Conference on Neural Information Processing Systems* (**NeurIPS Spotlight**)</span>, 2024   
    [[arXiv](https://arxiv.org/abs/2403.02993), [pdf](https://openreview.net/pdf?id=hS1jvV3Dk3)]
    <details>
        <summary>Abstract</summary>
        The efficacy of large language models (LLMs) in understanding and generating natural language has aroused a wide interest in developing prompt-based methods to harness the power of black-box LLMs, especially through the lens of in-context learning. Existing methods usually prioritize a global optimization for finding the global optimum of prompts, which however will perform poorly in certain tasks. This thus motivates us to re-think the necessity of finding a global optimum in prompt optimization. To answer this, we conduct a thorough empirical study on prompt optimization and draw two major insights. Contrasting with the rarity of global optimum, local optima are usually prevalent and well-performed, which can be more worthwhile for efficient prompt optimization (Insight I). The choice of the input domain, covering both the generation and the representation of prompts, affects the identification of well-performing local optima (Insight II). Inspired by these insights, we propose a novel algorithm, namely localized zeroth-order prompt optimization (ZOPO), which incorporates a Neural Tangent Kernel-based derived Gaussian process into standard zeroth-order optimization for an efficient search of well-performing local optima in prompt optimization. Remarkably, ZOPO outperforms existing baselines in terms of both the optimization performance and the query efficiency, which we demonstrate through extensive experiments.
    </details>  
- <span style="color: royalblue">Prompt Optimization with EASE? Efficient Ordering-aware Automated Selection of Exemplars.</span>  
    Zhaoxuan Wu, Xiaoqiang Lin, Zhongxiang Dai, Wenyang Hu, **Yao Shu**, See-Kiong Ng, Patrick Jaillet, Bryan Kian Hsiang Low  
    <span style="color: Red">Key Words: Prompt Optimization, Neural Bandit, Large Language Models</span>  
    In <span style="color: MediumSeaGreen">*In-Context Learning Workshop* @ **ICML**</span>, 2024  
    In <span style="color: MediumSeaGreen">*The 38th Conference on Neural Information Processing Systems* (**NeurIPS**)</span>, 2024   
    [[arXiv](https://arxiv.org/abs/2405.16122), [pdf](https://openreview.net/pdf?id=6uRrwWhZlM), [code](https://github.com/ZhaoxuanWu/EASE-Prompt-Optimization)]
    <details>
        <summary>Abstract</summary>
        Large language models (LLMs) have shown impressive capabilities in real-world applications. The capability of in-context learning (ICL) allows us to adapt an LLM to downstream tasks by including input-label exemplars in the prompt without model fine-tuning. However, the quality of these exemplars in the prompt greatly impacts performance, highlighting the need for an effective automated exemplar selection method. Recent studies have explored retrieval-based approaches to select exemplars tailored to individual test queries, which can be undesirable due to extra test-time computation and an increased risk of data exposure. Moreover, existing methods fail to adequately account for the impact of exemplar ordering on the performance. On the other hand, the impact of the instruction, another essential component in the prompt given to the LLM, is often overlooked in existing exemplar selection methods. To address these challenges, we propose a novel method named EASE, which leverages the hidden embedding from a pre-trained language model to represent ordered sets of exemplars and uses a neural bandit algorithm to optimize the sets of exemplars while accounting for exemplar ordering. Our EASE can efficiently find an ordered set of exemplars that performs well for all test queries from a given task, thereby eliminating test-time computation. Importantly, EASE can be readily extended to jointly optimize both the exemplars and the instruction. Through extensive empirical evaluations (including novel tasks), we demonstrate the superiority of EASE over existing methods, and reveal practical insights about the impact of exemplar selection on ICL, which may be of independent interest.
    </details>  
- <span style="color: royalblue">Data-Centric AI in the Age of Large Language Models.</span>  
    Xinyi Xu, Zhaoxuan Wu, Rui Qiao, Arun Verma, **Yao Shu**, Jingtan Wang, Xinyuan Niu, Zhenfeng He, Jiangwei Chen, Zijian Zhou, Gregory Kang Ruey Lau, Hieu Dao, Lucas Agussurja, Rachael Hwee Ling Sim, Xiaoqiang Lin, Wenyang Hu, Zhongxiang Dai, Pang Wei Koh, Bryan Kian Hsiang Low  
    <span style="color: Red">Key Words: Data-Centric AI, Large Language Models</span>  
    In <span style="color: MediumSeaGreen">*The 2024 Conference on Empirical Methods in Natural Language Processing* (**EMNLP** Findings)</span>, 2024  
    [[arXiv](https://arxiv.org/abs/2406.14473)]
    <details>
        <summary>Abstract</summary>
        This position paper proposes a data-centric viewpoint of AI research, focusing on large language models (LLMs). We start by making the key observation that data is instrumental in the developmental (e.g., pretraining and fine-tuning) and inferential stages (e.g., in-context learning) of LLMs, and yet it receives disproportionally low attention from the research community. We identify four specific scenarios centered around data, covering data-centric benchmarks and data curation, data attribution, knowledge transfer, and inference contextualization. In each scenario, we underscore the importance of data, highlight promising research directions, and articulate the potential impacts on the research community and, where applicable, the society as a whole. For instance, we advocate for a suite of data-centric benchmarks tailored to the scale and complexity of data for LLMs. These benchmarks can be used to develop new data curation methods and document research efforts and results, which can help promote openness and transparency in AI and LLM research.
    </details>  
- <span style="color: royalblue">Use Your INSTINCT: INSTruction optimization usIng Neural bandits Coupled with Transformers.</span>  
    Xiaoqiang Lin\*, Zhaoxuan Wu\*, Zhongxiang Dai#, Wenyang Hu, **Yao Shu**, See-Kiong Ng, Patrick Jaillet and Kian Hsiang Low  
    <span style="color: Red">Key Words: Prompt Optimization, Neural Bandit, Large Language Models</span>  
    In <span style="color: MediumSeaGreen">*Instruction Workshop* @ **NeurIPS**</span>, 2023  
    In <span style="color: MediumSeaGreen">*The 41st International Conference on Machine Learning* (**ICML**)</span>, 2024  
    <!-- Acceptance rate: 27.5%  -->
    [[arXiv](https://arxiv.org/abs/2310.02905), [pdf](https://openreview.net/pdf?id=RLENZ8pNnn), [code](https://github.com/xqlin98/INSTINCT)]  
    <details>
        <summary>Abstract</summary>
        Large language models (LLMs) have shown remarkable instruction-following capabilities and achieved impressive performances in various applications. However, the performances of LLMs depend heavily on the instructions given to them, which are typically manually tuned with substantial human efforts. Recent work has used the query-efficient Bayesian optimization (BO) algorithm to automatically optimize the instructions given to black-box LLMs. However, BO usually falls short when optimizing highly sophisticated (e.g., high-dimensional) objective functions, such as the functions mapping an instruction to the performance of an LLM. This is mainly due to the limited expressive power of the Gaussian process (GP) model which is used by BO as a surrogate to model the objective function. Meanwhile, it has been repeatedly shown that neural networks (NNs), especially pre-trained transformers, possess strong expressive power and can model highly complex functions. So, we adopt a neural bandit algorithm which replaces the GP in BO by an NN surrogate to optimize instructions for black-box LLMs. More importantly, the neural bandit algorithm allows us to naturally couple the NN surrogate with the hidden representation learned by a pre-trained transformer (i.e., an open-source LLM), which significantly boosts its performance. These motivate us to propose our INSTruction optimization usIng Neural bandits Coupled with Transformers (INSTINCT) algorithm. We perform instruction optimization for ChatGPT and use extensive experiments to show that our INSTINCT consistently outperforms the existing methods in different tasks, such as in various instruction induction tasks and the task of improving the zero-shot chain-of-thought instruction.
    </details>  
- <span style="color: royalblue">Data valuation in federated learning.</span>  
    Zhaoxuan Wu, Xinyi Xu, Rachael Hwee Ling Sim, **Yao Shu**, Xiaoqiang Lin, Lucas Agussurja, Zhongxiang Dai, See-Kiong Ng, Chuan-Sheng Foo, Patrick Jaillet, Trong Nghia Hoang and Kian Hsiang Low  
    <span style="color: Red">Key Words: Data Valuation, Federated Learning</span>  
    Chapter 15 of [*Federated Learning: Theory and Practice*](https://www.sciencedirect.com/science/article/abs/pii/B9780443190377000247), pages 281-296, Academic Press, 2024  
- <span style="color: royalblue">DAVINZ: Data Valuation using Deep Neural Networks at Initialization.</span>  
    Zhaoxuan Wu, **Yao Shu**, Bryan Kian Hsiang Low  
    <span style="color: Red">Key Words: Data Valuation, Generalization Bound, Neural Tangent Kernel</span>  
    In <span style="color: MediumSeaGreen">*The 39th International Conference on Machine Learning* (**ICML**)</span>, 2022  
    <!-- Acceptance rate: 21.9%  -->
    [[pdf](https://proceedings.mlr.press/v162/wu22j/wu22j.pdf), [code](https://github.com/ZhaoxuanWu/DAVINZ-DataValuation)] 
    <details>
        <summary>Abstract</summary>
        Recent years have witnessed a surge of interest in developing trustworthy methods to evaluate the value of data in many real-world applications, e.g., collaborative machine learning, data marketplaces, etc. Existing data valuation methods typically valuate data using the generalization performance of converged machine learning models after their long-term model training, making data valuation on large complex deep neural networks (DNNs) unaffordable. To this end, we theoretically derive a domain-aware generalization bound to estimate the generalization performance of DNNs without model training. We then exploit this theoretically derived generalization bound to develop a novel training-free data valuation method named data valuation at initialization (DAVINZ) on DNNs, which consistently achieves remarkable effectiveness and efficiency in practice. Moreover, our training-free DAVINZ, surprisingly, can even theoretically and empirically enjoy the desirable properties that training-based data valuation methods usually attain, making it more trustworthy in practice. 
    </details>  

### Model-Centric
- <span style="color: royalblue">Flexora: Flexible Low Rank Adaptation for Large Language Models.</span>  
    Chenxing Wei\*, **Yao Shu**\*, Ying Tiffany He, Fei Richard Yu  
    <span style="color: Red">Key Words: Layer Selection, Parameter-Efficient Fine-Tuning, Large Language Models</span>  
    In <span style="color: MediumSeaGreen">*Fine-Tuning in Modern Machine Learning Workshop* @ **NeurIPS**</span>, 2024  
    [[arXiv](https://arxiv.org/pdf/2408.10774)]  
    <details>
        <summary>Abstract</summary>
        Large Language Models (LLMs) are driving advancements in artificial intelligence by increasing the scale of model parameters, which has significantly enhanced generalization ability and unlocked new capabilities in practice. However, their performance in specific downstream tasks is usually hindered by their knowledge boundaries on these tasks. Thus, fine-tuning techniques, especially the widely used Low-Rank Adaptation (LoRA) method, have been introduced to expand the boundaries on these tasks, whereas LoRA would underperform on certain tasks owing to its potential overfitting on these tasks. To overcome this overfitting and improve the performance of LoRA, we propose the flexible low rank adaptation (Flexora) method to automatically and flexibly select the most important layers needing to be fine-tuned to achieve the best performance on different downstream tasks. Specifically, Flexora firstly frames this layer selection problem as a well-defined hyperparameter optimization (HPO) problem, then addresses it using the unrolled differentiation (UD) method, and finally selects the most useful layers based on the optimized hyperparameters. Our extensive experiments on many pretrained models and natural language tasks show that Flexora is able to consistently improve over the existing baselines, indicating the effectiveness of our Flexora in practice. We additionally provide insightful theoretical results and many ablation studies to deliver a comprehensive understanding of our Flexora.
    </details>  
- <span style="color: royalblue">Robustifying and Boosting Training-Free Neural Architecture Search.</span>  
    Zhenfeng He, **Yao Shu**#, Zhongxiang Dai, Bryan Kian Hsiang Low  
    <span style="color: Red">Key Words: Training-Free Neural Architecture Search</span>  
    In <span style="color: MediumSeaGreen">*The 12th International Conference on Learning Representations* (**ICLR**)</span>, 2024  
    <!-- Acceptance rate: 31%  -->
    [[arXiv](https://arxiv.org/abs/2403.07591), [pdf](https://openreview.net/pdf?id=qPloNoDJZn), [code](https://github.com/hzf1174/RoBoT)]  
    <details>
        <summary>Abstract</summary>
        Neural architecture search (NAS) has become a key component of AutoML and a standard tool to automate the design of deep neural networks. Recently, training-free NAS as an emerging paradigm has successfully reduced the search costs of standard training-based NAS by estimating the true architecture performance with only training-free metrics. Nevertheless, the estimation ability of these metrics typically varies across different tasks, making it challenging to achieve robust and consistently good search performance on diverse tasks with only a single training-free metric. Meanwhile, the estimation gap between training-free metrics and the true architecture performances limits training-free NAS to achieve superior performance. To address these challenges, we propose the robustifying and boosting training-free NAS (RoBoT) algorithm which (a) employs the optimized combination of existing training-free metrics explored from Bayesian optimization to develop a robust and consistently better-performing metric on diverse tasks, and (b) applies greedy search, i.e., the exploitation, on the newly developed metric to bridge the aforementioned gap and consequently to boost the search performance of standard training-free NAS further. Remarkably, the expected performance of our RoBoT can be theoretically guaranteed, which improves over the existing training-free NAS under mild conditions with additional interesting insights. Our extensive experiments on various NAS benchmark tasks yield substantial empirical evidence to support our theoretical results.
    </details>  
- <span style="color: royalblue">Unifying and Boosting Gradient-Based Training-Free Neural Architecture Search.</span>  
    **Yao Shu**, Zhongxiang Dai, Zhaoxuan Wu, Bryan Kian Hsiang Low  
    <span style="color: Red">Key Words: Training-Free Neural Architecture Search, Generalization Bound, Neural Tangent Kernel</span>  
    In <span style="color: MediumSeaGreen">*The 36th Conference on Neural Information Processing Systems* (**NeurIPS**)</span>, 2022  
    <!-- Acceptance rate: 25.6%  -->
    [[arXiv](https://arxiv.org/abs/2201.09785), [pdf](https://arxiv.org/pdf/2201.09785.pdf), [code](https://github.com/shuyao95/HNAS)]  
    <details>
        <summary>Abstract</summary>
        Neural architecture search (NAS) has gained immense popularity owing to its ability to automate neural architecture design. A number of training-free metrics are recently proposed to realize NAS without training, hence making NAS more scalable. Despite their competitive empirical performances, a unified theoretical understanding of these training-free metrics is lacking. As a consequence, (a) the relationships among these metrics are unclear, (b) there is no theoretical interpretation for their empirical performances, and (c) there may exist untapped potential in existing training-free NAS, which probably can be unveiled through a unified theoretical understanding. To this end, this paper presents a unified theoretical analysis of gradient-based training-free NAS, which allows us to (a) theoretically study their relationships, (b) theoretically guarantee their generalization performances, and (c) exploit our unified theoretical understanding to develop a novel framework named hybrid NAS (HNAS) which consistently boosts training-free NAS in a principled way. Remarkably, HNAS can enjoy the advantages of both training-free (i.e., superior search efficiency) and training-based (i.e., remarkable search effectiveness) NAS, which we have demonstrated through extensive experiments.
    </details>  
- <span style="color: royalblue">Neural Ensemble Search via Bayesian Sampling.</span>  
    **Yao Shu**, Yizhou Chen, Zhongxiang Dai, Bryan Kian Hsiang Low  
    <span style="color: Red">Key Words: Neural Ensemble Search, Bayesian Posterior</span>  
    In <span style="color: MediumSeaGreen">*The 38th Conference on Uncertainty in Artificial Intelligence* (**UAI**)</span>, 2022  
    <!-- Acceptance rate: 32.3%  -->
    [[arXiv](https://arxiv.org/abs/2109.02533), [pdf](https://openreview.net/pdf?id=Bh4lBPUjqg9)]  
    <details>
        <summary>Abstract</summary>
        Recently, neural architecture search (NAS) has been applied to automate the design of neural networks in real-world applications. A large number of algorithms have been developed to improve the search cost or the performance of the final selected architectures in NAS. Unfortunately, these NAS algorithms aim to select only one single well-performing architecture from their search spaces and thus have overlooked the capability of neural network ensemble (i.e., an ensemble of neural networks with diverse architectures) in achieving improved performance over a single final selected architecture. To this end, we introduce a novel neural ensemble search algorithm, called neural ensemble search via Bayesian sampling (NESBS), to effectively and efficiently select well-performing neural network ensembles from a NAS search space. In our extensive experiments, NESBS algorithm is shown to be able to achieve improved performance over state-of-the-art NAS algorithms while incurring a comparable search cost, indicating the superior of our NESBS algorithm over these conventional NAS algorithms in practice. 
    </details>  
- <span style="color: royalblue">NASI: Label- and Data-agnostic Neural Architecture Search at Initialization.</span>  
    **Yao Shu**, Shaofeng Cai, Zhongxiang Dai, Beng Chin Ooi, Bryan Kian Hsiang Low  
    <span style="color: Red">Key Words: Training-Free Neural Architecture Search, Neural Tangent Kernel</span>  
    In <span style="color: MediumSeaGreen">*The 10th International Conference on Learning Representations* (**ICLR**)</span>, 2022  
    <!-- Acceptance rate: 32.3%  -->
    [[arXiv](https://arxiv.org/abs/2109.00817), [pdf](https://openreview.net/pdf?id=v-v1cpNNK_v)]  
    <details>
        <summary>Abstract</summary>
        Recent years have witnessed a surging interest in Neural Architecture Search (NAS). Various algorithms have been proposed to improve the search efficiency and effectiveness of NAS, i.e., to reduce the search cost and improve the generalization performance of the selected architectures, respectively. However, the search efficiency of these algorithms is severely limited by the need for model training during the search process. To overcome this limitation, we propose a novel NAS algorithm called NAS at Initialization (NASI) that exploits the capability of a Neural Tangent Kernel in being able to characterize the performance of candidate architectures at initialization, hence allowing model training to be completely avoided to boost the search efficiency. Besides the improved search efficiency, NASI also achieves competitive search effectiveness on various datasets like CIFAR-10/100 and ImageNet. Further, NASI is shown to be label- and data-agnostic under mild conditions, which guarantees the transferability of architectures selected by our NASI over different datasets. 
    </details>  
- <span style="color: royalblue">Dynamic Routing Networks.</span>  
    Shaofeng Cai, **Yao Shu**, Wei Wang  
    <span style="color: Red">Key Words: Architecture Design, Mixture of Branch</span>  
    In <span style="color: MediumSeaGreen">*Proceedings of the IEEE/CVF Winter Conference on Applications of Computer Vision* (**WACV**)</span>, 2021  
    <details>
        <summary>Abstract</summary>
        The deployment of deep neural networks in real-world applications is mostly restricted by their high inference costs. Extensive efforts have been made to improve the accuracy with expert-designed or algorithm-searched architectures. However, the incremental improvement is typically achieved with increasingly more expensive models that only a small portion of input instances really need. Inference with a static architecture that processes all input instances via the same transformation would thus incur unnecessary computational costs. Therefore, customizing the model capacity in an instance-aware manner is much needed for higher inference efficiency. In this paper, we propose Dynamic Routing Networks (DRNets), which support efficient instance-aware inference by routing the input instance to only necessary transformation branches selected from a candidate set of branches for each connection between transformation nodes. The branch selection is dynamically determined via the corresponding branch importance weights, which are first generated from lightweight hypernetworks (RouterNets) and then recalibrated with Gumbel-Softmax before the selection. Extensive experiments show that DRNets can reduce a substantial amount of parameter size and FLOPs during inference with prediction performance comparable to state-of-the-art architectures.
    </details>  
- <span style="color: royalblue">Understanding Architectures Learnt by Cell-based Neural Architecture Search.</span>  
    **Yao Shu**, Wei Wang, Shaofeng Cai  
    <span style="color: Red">Key Words: Neural Architecture Search, Optimization, Generalization</span>  
    In <span style="color: MediumSeaGreen">*The 8th International Conference on Learning Representations* (**ICLR**)</span>, 2020  
    <!-- Acceptance rate: 26.5%  -->
    [[arXiv](https://arxiv.org/abs/1909.09569), [pdf](https://openreview.net/pdf?id=BJxH22EKPS), [code](https://github.com/shuyao95/Understanding-NAS.git)]  
    <details>
        <summary>Abstract</summary>
        Neural architecture search (NAS) searches architectures automatically for given tasks, e.g., image classification and language modeling. Improving the search efficiency and effectiveness have attracted increasing attention in recent years. However, few efforts have been devoted to understanding the generated architectures. In this paper, we first reveal that existing NAS algorithms (e.g., DARTS, ENAS) tend to favor architectures with wide and shallow cell structures. These favorable architectures consistently achieve fast convergence and are consequently selected by NAS algorithms. Our empirical and theoretical study further confirms that their fast convergence derives from their smooth loss landscape and accurate gradient information. Nonetheless, these architectures may not necessarily lead to better generalization performance compared with other candidate architectures in the same search space, and therefore further improvement is possible by revising existing NAS algorithms.
    </details>  

### Training-Centric
- <span style="color: royalblue">Ferret: Federated Full-Parameter Tuning at Scale for Large Language Models.</span>  
    **Yao Shu\***, Wenyang Hu\*, See-Kiong Ng, Bryan Kian Hsiang Low, Fei Richard Yu   
    <span style="color: Red">Key Words: Large Language Models, Federated Full-Parameter Tuning</span>  
    In <span style="color: MediumSeaGreen">*Federated Foundation Models Workshop* @ **NeurIPS (Oral)**</span>, 2024  
    [[HuggingFace](https://huggingface.co/papers/2409.06277), [arXiv](https://arxiv.org/abs/2409.06277), [code](https://github.com/allen4747/Ferret)]
    <details>
        <summary>Abstract</summary>
        Large Language Models (LLMs) have become indispensable in numerous real-world applications. Unfortunately, fine-tuning these models at scale, especially in federated settings where data privacy and communication efficiency are critical, presents significant challenges. Existing methods often resort to parameter-efficient fine-tuning (PEFT) to mitigate communication overhead, but this typically comes at the cost of model accuracy. To address these limitations, we propose federated full-parameter tuning at scale for LLMs (Ferret), the first first-order method with shared randomness to enable scalable full-parameter tuning of LLMs across decentralized data sources while maintaining competitive model accuracy. Ferret accomplishes this through three aspects: (1) it employs widely applied first-order methods for efficient local updates; (2) it projects these updates into a low-dimensional space to considerably reduce communication overhead; and (3) it reconstructs local updates from this low-dimensional space with shared randomness to facilitate effective full-parameter global aggregation, ensuring fast convergence and competitive final performance. Our rigorous theoretical analyses and insights along with extensive experiments, show that Ferret significantly enhances the scalability of existing federated full-parameter tuning approaches by achieving high computational efficiency, reduced communication overhead, and fast convergence, all while maintaining competitive model accuracy. Our implementation is available at https://github.com/allen4747/Ferret.
    </details>  

## Other Topics
- <span style="color: royalblue">Tight Lower Complexity Bounds for Strongly Convex Finite-Sum Optimization.</span>  
    Min Zhang, **Yao Shu**, Kun He  
    <span style="color: Red">Key Words: First-Order Optimization, Lower Bound</span>  
    [[arXiv](https://arxiv.org/abs/2010.08766)]
    <details>
        <summary>Abstract</summary>
        Finite-sum optimization plays an important role in the area of machine learning, and hence has triggered a surge of interest in recent years. To address this optimization problem, various randomized incremental gradient methods have been proposed with guaranteed upper and lower complexity bounds for their convergence. Nonetheless, these lower bounds rely on certain conditions: deterministic optimization algorithm, or fixed probability distribution for the selection of component functions. Meanwhile, some lower bounds even do not match the upper bounds of the best known methods in certain cases. To break these limitations, we derive tight lower complexity bounds of randomized incremental gradient methods, including SAG, SAGA, SVRG, and SARAH, for two typical cases of finite-sum optimization. Specifically, our results tightly match the upper complexity of Katyusha or VRADA when each component function is strongly convex and smooth, and tightly match the upper complexity of SDCA without duality and of KatyushaX when the finite-sum function is strongly convex and the component functions are average smooth.
    </details>  
- <span style="color: royalblue">Effective and Efficient Dropout for Deep Convolutional Neural Networks.</span>  
    Shaofeng Cai, **Yao Shu**, Wei Wang, Meihui Zhang, Gang Chen, Beng Chin Ooi  
    <span style="color: Red">Key Words: Dropout, Regularization, Generalization</span>  
    [[arXiv](https://arxiv.org/abs/1904.03392)]  
    <details>
        <summary>Abstract</summary>
        Convolutional Neural networks (CNNs) based applications have become ubiquitous, where proper regularization is greatly needed. To prevent large neural network models from overfitting, dropout has been widely used as an efficient regularization technique in practice. However, many recent works show that the standard dropout is ineffective or even detrimental to the training of CNNs. In this paper, we revisit this issue and examine various dropout variants in an attempt to improve existing dropout-based regularization techniques for CNNs. We attribute the failure of standard dropout to the conflict between the stochasticity of dropout and its following Batch Normalization (BN), and propose to reduce the conflict by placing dropout operations right before the convolutional operation instead of BN, or totally address this issue by replacing BN with Group Normalization (GN). We further introduce a structurally more suited dropout variant Drop-Conv2d, which provides more efficient and effective regularization for deep CNNs. These dropout variants can be readily integrated into the building blocks of CNNs and implemented in existing deep learning platforms. Extensive experiments on benchmark datasets including CIFAR, SVHN and ImageNet are conducted to compare the existing building blocks and the proposed ones with dropout training. Results show that our building blocks improve over state-of-the-art CNNs significantly, which is mainly due to the better regularization and implicit model ensemble effect.
    </details>  
- <span style="color: royalblue">Efficient Memory Management for GPU-based Deep Learning Systems.</span>  
    Junzhe Zhang, Sai Ho Yeung, **Yao Shu**, Bingsheng He, Wei Wang  
    <span style="color: Red">Key Words: Memory-Efficient Training</span>  
    [[arXiv](https://arxiv.org/abs/1903.06631)]  
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