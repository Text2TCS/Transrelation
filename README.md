# Text2TCS CogaLex VI submission

This is a description of our system submitted to the CogaLex VI shared task.
The labeled test sets can be found in the folder “annotated test sets”. The "models" folder contains the trained models that were used for the final annotation.

### TODO - Voting

### TODO - Contrast Maps 
In order to improve the accuracy of the prediction provided by the XLM-RoBERTa based subsystem, we added a voting system to our pipeline, which makes use of the concept of Contrast Maps as shown in [1]. 
The networks introduced by Samenko et al. [1] aim to further distinguish synonyms from antonyms using only information already present in modern word embeddings.
To enable a multilingual and light-weight model, we adapted the system to use mBPEmb [2] as our word embeddings for training and inference. This enabled us to train the several proposed Networks in three languages, improving accuracy for less performant and hitherto unseen languages.
The Siamese Triplet Network with annealing provided the highest performance of the proposed networks. 
A very low learning-rate was necessary to avoid overfitting on the rather low amount of training data due to the challenge restrictions. The following hyperparameters were used for training the system:
-	Optimizer: Adam
-	Learning rate: 1e-4
-	Epochs:
-	Batch size:
-	Loss function:
-	With_Scheduler: False


### XLM-RoBERTa 

This subsystem makes use of the multilingual language model XLM-RoBERTa [3]. We use the implementation provided by the transformers library, which offers the XLM-RoBERTa model pretained on 100 different languages using CommonCrawl data [4]. A linear layer is added on top of the pooled output in order to allow classification. 
The model was trained on the training data provided for CogALex VI shared task, with the training being performed on all three languages at the same time. Hyperparameters were finetuned on the given validation set. The best results were achieved with the following Hyperparameters
-	Optimizer: AdamW
-	Learning rate: 2e-5
-	Epsilon: 1e-8
-	Epochs: 7
-	Batch size: 32
-	Warm up steps: 0
-	Weight Decay: 0
- 	Model size: Base   

### References
[1] Samenko, I., Tikhonov, A., & Yamshchikov, I. P. 2020. Synonyms and Antonyms: Embedded Conflict. ArXiv:2004.12835v1 [Cs]. Retrieved from http://arxiv.org/abs/2004.12835v1

[2] Heinzerling, B., & Strube, M. 2018. BPEMB: Tokenization-free pre-trained subword embeddings in 275 languages. LREC 2018 - 11th International Conference on Language Resources and Evaluation, 2989–2993. Retr>

[3] Conneau, A., Khandelwal, K., Goyal, N., Chaudhary, V., Wenzek, G., Guzmán, F., ... & Stoyanov, V. (2019). Unsupervised cross-lingual representation learning at scale. arXiv preprint arXiv:1911.02116.

[4] Wolf, T., Debut, L., Sanh, V., Chaumond, J., Delangue, C., Moi, A., ... & Brew, J. (2019). HuggingFace's Transformers: State-of-the-art Natural Language Processing. ArXiv, arXiv-1910.
