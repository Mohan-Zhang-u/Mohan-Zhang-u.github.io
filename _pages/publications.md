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


### [To Paraphrase or Not To Paraphrase: User-Controllable Selective Paraphrase Generation](https://arxiv.org/abs/2008.09290)
***Mohan Zhang**, Luchen Tan, Zhengkai Tu, Zihang Fu, Kun Xiong, Ming Li and Jimmy Lin* <br/>
#### At University of Toronto and RSVP.ai
Abstract: In this article, we propose a paraphrase generation technique to keep the key phrases in source sentences during paraphrasing. We also develop a model called TAGPA with such technique, which has multiple pre-configured or trainable key phrase detector and a paraphrase generator. The paraphrase generator aims to keep the key phrases and increase the diversity of the paraphrased sentences. The key phrases can be entities provided by our user, like company names, people's names, domain-specific terminologies, etc., or can be learned from a given dataset. <br/>
Pending more experiment results and preparing for submission.

### [PtEQA: Domain Specific Question Answering with Document Extraction Utilizing Pre-trained Weights](https://github.com/Mohan-Zhang-u/MyQA/blob/master/PtEQA__Domain_Specific_Question_Answering_with_Document_Extraction_Utilizing_Pre_trained_Weights_LREC.pdf)
***Mohan Zhang**, Sudeep Singh and Pawel Maciszewski* <br/>
#### At Exxon Mobil and University of Toronto
Abstract: This paper demonstrated a methodology to build a question and answering system based on unlabeled large corpus. The model has two components: Document Retriever and Answer Extractor. Document Retriever used bigram hashing and TF-IDF matching to pick the most relevant articles regarding the question; Answer Extractor used the Deep Bidirectional Transformers introduced by BERT to locate the answer from relevant articles extracted by Document Retriever. Training or fine-tuning is not required for this machine reading system, though it can help improve Q\&A performance on domain-specific questions.