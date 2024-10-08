---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

<!-- {% if author.googlescholar %}
  You can also find my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u>
{% endif %}

{% include base_path %}

{% for post in site.publications reversed %}
  {% include archive-single.html %}
{% endfor %} -->

### [(NeurIPS 2022) SMPL: Simulated Industrial Manufacturing and Process Control Learning Environments](https://openreview.net/forum?id=TscdNx8udf5)
***Mohan Zhang**, Xiaozhou Wang, Benjamin Decardi-Nelson, Bo Song, An Zhang, Jinfeng Liu, Sile Tao, Jiayi Cheng, Xiaohong Liu, DengDeng Yu, Matthew Poon, Animesh Garg* <br/>
<!-- #### At the University of Toronto and Quartic.ai -->
Abstract: Traditional biological and pharmaceutical manufacturing plants are controlled by human workers or pre-defined thresholds. Modernized factories have advanced process control algorithms such as model predictive control (MPC). However, there is little exploration of applying deep reinforcement learning to control manufacturing plants. One of the reasons is the lack of high fidelity simulations and standard APIs for benchmarking. To bridge this gap, we develop an easy-to-use library that includes five high-fidelity simulation environments: BeerFMTEnv, ReactorEnv, AtropineEnv, PenSimEnv and mAbEnv, which cover a wide range of manufacturing processes. We build these environments on published dynamics models. Furthermore, we benchmark online and offline, model-based and model-free reinforcement learning algorithms for comparisons of follow-up research.


### [(EACL 2021) Don't Change Me! User-Controllable Selective Paraphrase Generation](https://www.aclweb.org/anthology/2021.eacl-main.307/)
***Mohan Zhang**, Luchen Tan, Zhengkai Tu, Zihang Fu, Kun Xiong, Ming Li and Jimmy Lin* <br/>
<!-- #### At the University of Toronto and RSVP.ai -->
Abstract: In the paraphrase generation task, source sentences often contain phrases that should not be altered. Which phrases, however, can be context dependent and can vary by application. Our solution to this challenge is to provide the user with explicit tags that can be placed around any arbitrary segment of text to mean "don't change me!" when generating a paraphrase; the model learns to explicitly copy these phrases to the output. The contribution of this work is a novel data generation technique using distant supervision that allows us to start with a pretrained sequence-to-sequence model and fine-tune a paraphrase generator that exhibits this behavior, allowing user-controllable paraphrase generation. Additionally, we modify the loss during fine-tuning to explicitly encourage diversity in model output. Our technique is language agnostic, and we report experiments in English and Chinese.

### [PtEQA: Domain Specific Question Answering with Document Extraction Utilizing Pre-trained Weights](https://github.com/Mohan-Zhang-u/MyQA/blob/master/PtEQA__Domain_Specific_Question_Answering_with_Document_Extraction_Utilizing_Pre_trained_Weights_LREC.pdf)
***Mohan Zhang**, Sudeep Singh and Pawel Maciszewski* <br/>
<!-- #### At the University of Toronto and Exxon Mobil -->
Abstract: This paper demonstrated a methodology to build a question and answering system based on an unlabeled large corpus. The model has two components: Document Retriever and Answer Extractor. Document Retriever used bigram hashing and TF-IDF matching to pick the most relevant articles regarding the question; Answer Extractor used the Deep Bidirectional Transformers introduced by BERT to locate the answer from relevant articles extracted by Document Retriever. Training or fine-tuning is not required for this machine reading system, though it can help improve Q\&A performance on domain-specific questions.

### [Latent Dirichlet Allocation with Residual Convolutional Neural Network Applied in Evaluating Credibility of Chinese Listed Companies](https://scholar.google.ca/scholar?hl=en&as_sdt=0%2C5&q=Latent+Dirichlet+Allocation+with+Residual+Convolutional+Neural+Network+Applied+in+Evaluating+Credibility+of+Chinese+Listed+Companies)
***Mohan Zhang**, Zhichao Luo and Hai Lu* <br/>
<!-- #### At the University of Toronto -->
Abstract: This project demonstrated a methodology to estimating cooperate credibility with a Natural Language Processing approach. As cooperate transparency impacts both the credibility and possible future earnings of the firm, it is an important factor to be considered by banks and investors on risk assessments of listed firms. This approach of estimating cooperate credibility can bypass human bias and inconsistency in the risk assessment, the use of large quantitative data and neural network models provides more accurate estimation in a more efficient manner compare to manual assessment. At the beginning, the model will employs Latent Dirichlet Allocation and THU Open Chinese Lexicon from Tsinghua University to classify topics in articles which are potentially related to corporate credibility. Then with the keywords related to each topics, we trained a residual convolutional neural network with data labeled according to surveys of fund manager and accountant's opinion on corporate credibility. After the training, we run the model with preprocessed news reports regarding to all of the 3065 listed companies, the model is supposed to give back companies ranking based on the level of their transparency.
