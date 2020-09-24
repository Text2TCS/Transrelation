# Text2TCS CogaLex VI submission

This is a description of our system submitted to the CogaLex VI shared task.

TODO - Voting

TODO - Contrast Maps 

XLM-RoBERTa 
This subsystem makes use of the multilingual language model XLM-RoBERTa [1]. We use the implementation provided by the transformers library, which offers the XLM-RoBERTa model pretained on 100 different languages using CommonCrawl data [2]. A linear layer is added on top of the pooled output in order to allow classification. 
The model was trained on the training data provided for CogALex VI shared task, with the training being performed on all three languages at the same time. Hyperparameters were finetuned on the given validation set. The best results were achieved with the following Hyperparameters
-	Optimizer: AdamW
-	Learning rate: 2e-5
-	Epsilon: 1e-8
-	Epochs: 7
-	Batch size: 32
-	Warm up steps: 0
-	Weight Decay: 0
- 	Model size: Base 

The labeled test sets can be found in the folder “annotated test sets”. The "models" folder contains the trained models that were used for the final annotation.  

[1] Conneau, A., Khandelwal, K., Goyal, N., Chaudhary, V., Wenzek, G., Guzmán, F., ... & Stoyanov, V. (2019). Unsupervised cross-lingual representation learning at scale. arXiv preprint arXiv:1911.02116.
[2] Wolf, T., Debut, L., Sanh, V., Chaumond, J., Delangue, C., Moi, A., ... & Brew, J. (2019). HuggingFace's Transformers: State-of-the-art Natural Language Processing. ArXiv, arXiv-1910.
