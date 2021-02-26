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


### [(EACL 2021) Don't Change Me! User-Controllable Selective Paraphrase Generation](https://arxiv.org/abs/2008.09290)
***Mohan Zhang**, Luchen Tan, Zhengkai Tu, Zihang Fu, Kun Xiong, Ming Li and Jimmy Lin* <br/>
#### At University of Toronto and RSVP.ai
Abstract: In the paraphrase generation task, source sentences often contain phrases that should not be altered. Which phrases, however, can be context dependent and can vary by application. Our solution to this challenge is to provide the user with explicit tags that can be placed around any arbitrary segment of text to mean "don't change me!" when generating a paraphrase; the model learns to explicitly copy these phrases to the output. The contribution of this work is a novel data generation technique using distant supervision that allows us to start with a pretrained sequence-to-sequence model and fine-tune a paraphrase generator that exhibits this behavior, allowing user-controllable paraphrase generation. Additionally, we modify the loss during fine-tuning to explicitly encourage diversity in model output. Our technique is language agnostic, and we report experiments in English and Chinese.

### [PtEQA: Domain Specific Question Answering with Document Extraction Utilizing Pre-trained Weights](https://github.com/Mohan-Zhang-u/MyQA/blob/master/PtEQA__Domain_Specific_Question_Answering_with_Document_Extraction_Utilizing_Pre_trained_Weights_LREC.pdf)
***Mohan Zhang**, Sudeep Singh and Pawel Maciszewski* <br/>
#### At Exxon Mobil and University of Toronto
Abstract: This paper demonstrated a methodology to build a question and answering system based on unlabeled large corpus. The model has two components: Document Retriever and Answer Extractor. Document Retriever used bigram hashing and TF-IDF matching to pick the most relevant articles regarding the question; Answer Extractor used the Deep Bidirectional Transformers introduced by BERT to locate the answer from relevant articles extracted by Document Retriever. Training or fine-tuning is not required for this machine reading system, though it can help improve Q\&A performance on domain-specific questions.