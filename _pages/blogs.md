---
permalink: /blogs/
title: "Blogs"
excerpt: "Blogs"
author_profile: true
---

### Tranformers' pipeline refinement
*2021 Mar. 14*

tranformers' original Pipeline does not include batchify and truncate the input, but you can fix this with newly defined classes, exampled as below:

```python
from transformers.tokenization_utils_base import TruncationStrategy
import more_itertools
import math


class RefinedTextClassificationPipeline(TextClassificationPipeline):

    def __init__(self, truncation=TruncationStrategy.DO_NOT_TRUNCATE, max_length=512, batch_size=128, **kwargs):
        super().__init__(**kwargs)
        self.truncation = truncation  # whether to truncate the input sequence or not
        self.max_length = max_length  # what is the max sequence length if want to truncate 

    def _parse_and_tokenize(
        self, inputs, padding=True, add_special_tokens=True, **kwargs
    ):
        """
        Parse arguments and tokenize
        """
        # Parse arguments
        inputs = self.tokenizer(
            inputs,
            add_special_tokens=add_special_tokens,
            return_tensors=self.framework,
            padding=padding,
            truncation=self.truncation,
            max_length=self.max_length,
        )

        return inputs

    def __call__(self, *args, **kwargs):
        input_list = inputs
        # do whatever customized unwrap to the input you need here, assume now you have a input_list
        unwraped_inputs_dicts = [None] * (math.ceil(len(input_list)/prediction_batch_size)) 
        for i, inputs in tqdm(enumerate(more_itertools.chunked(input_list, prediction_batch_size))):
            inputs = self._parse_and_tokenize(inputs, *args, **kwargs)
            unwraped_inputs_dicts[i] = self._forward(inputs)
            # wrap unwraped_inputs_dicts up to the dictionary form again
        inputs = input_list
```


### Do Not Use the Transformers Custom Loss Example
*2021 Mar. 10*

the [example code here](https://huggingface.co/transformers/main_classes/trainer.html#trainingarguments)
```python
from transformers import Trainer
class MyTrainer(Trainer):
    def compute_loss(self, model, inputs):
        labels = inputs.pop("labels")
        outputs = model(**inputs)
        logits = outputs[0]
        return my_custom_loss(logits, labels)
```
will give you this error
```bash
  File "/home/xlova/anaconda3/lib/python3.8/site-packages/transformers/trainer.py", line 989, in train
    self._maybe_log_save_evaluate(tr_loss, model, trial, epoch)
  File "/home/xlova/anaconda3/lib/python3.8/site-packages/transformers/trainer.py", line 1058, in _maybe_log_save_evaluate
    metrics = self.evaluate()
  File "/home/xlova/anaconda3/lib/python3.8/site-packages/transformers/trainer.py", line 1506, in evaluate
    output = self.prediction_loop(
  File "/home/xlova/anaconda3/lib/python3.8/site-packages/transformers/trainer.py", line 1630, in prediction_loop
    loss, logits, labels = self.prediction_step(model, inputs, prediction_loss_only, ignore_keys=ignore_keys)
  File "/home/xlova/anaconda3/lib/python3.8/site-packages/transformers/trainer.py", line 1762, in prediction_step
    labels = nested_detach(tuple(inputs.get(name) for name in self.label_names))
  File "/home/xlova/anaconda3/lib/python3.8/site-packages/transformers/trainer_pt_utils.py", line 111, in nested_detach
    return type(tensors)(nested_detach(t) for t in tensors)
  File "/home/xlova/anaconda3/lib/python3.8/site-packages/transformers/trainer_pt_utils.py", line 111, in <genexpr>
    return type(tensors)(nested_detach(t) for t in tensors)
  File "/home/xlova/anaconda3/lib/python3.8/site-packages/transformers/trainer_pt_utils.py", line 112, in nested_detach
    return tensors.detach()
AttributeError: 'NoneType' object has no attribute 'detach'
```

Solution is, instead of pop, do
```python
from transformers import Trainer
class MyTrainer(Trainer):
    def compute_loss(self, model, inputs):
        labels = inputs.get("labels")
        outputs = model(**inputs)
        logits = outputs.get('logits')
        return my_custom_loss(logits, labels)
```






