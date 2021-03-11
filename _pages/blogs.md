---
permalink: /blogs/
title: "Blogs"
excerpt: "Blogs"
author_profile: true
---

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








