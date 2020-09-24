# Text2TCS CogALex VI submission

This is a description of our system submitted to the CogaLex VI shared task (https://sites.google.com/site/cogalexvisharedtask/). We use a single multilingual model in order to annotate the four different test sets. 

The labeled test sets can be found in the folder “annotated test sets”.

### XLM-RoBERTa 

Our system makes use of the multilingual language model XLM-RoBERTa [1]. We use the implementation provided by the transformers library, which offers the XLM-RoBERTa model pretained on 100 different languages using CommonCrawl data [2]. A linear layer is added on top of the pooled output in order to allow classification. 
The model was trained on the training data provided for CogALex VI shared task, with the training being performed on all three languages at the same time. Hyperparameters were finetuned on the given validation set. The best results were achieved with the following Hyperparameters
-	Optimizer: AdamW
-	Learning rate: 2e-5
-	Epsilon: 1e-8
-	Epochs: 7
-	Batch size: 32
-	Warm up steps: 0
-	Weight Decay: 0
- 	Model size: Base   

### Results on Validation Set
With XLMR Model

Chinese
|Class|Precision|Recall|F1|Support|
|---|---|---|---|---|
|SYN| 0.862| 0.822| 0.841| 129|
|HYP| 0.938| 0.841| 0.887| 145|
|HYP| 0.877| 0.838| 0.857| 136|
|Overall| 0.894| 0.834| 0.863||

English
|Class|Precision|Recall|F1|Support|
|---|---|---|---|---|
|SYN| 0.492| 0.463| 0.477| 259|
|HYP| 0.597| 0.473| 0.528| 292|
|HYP| 0.801| 0.497| 0.613| 308|
|Overall| 0.639| 0.478| 0.543||

German
|Class|Precision|Recall|F1|Support|
|---|---|---|---|---|
|SYN| 0.507| 0.419| 0.459| 272|
|HYP| 0.595| 0.459| 0.518| 294|
|HYP| 0.673| 0.411| 0.510| 275|
|Overall| 0.592| 0.430| 0.496||


### References
[1] Conneau, A., Khandelwal, K., Goyal, N., Chaudhary, V., Wenzek, G., Guzmán, F., ... & Stoyanov, V. (2019). Unsupervised cross-lingual representation learning at scale. arXiv preprint arXiv:1911.02116.

[2] Wolf, T., Debut, L., Sanh, V., Chaumond, J., Delangue, C., Moi, A., ... & Brew, J. (2019). HuggingFace's Transformers: State-of-the-art Natural Language Processing. ArXiv, arXiv-1910.
