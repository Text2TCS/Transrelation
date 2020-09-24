# Text2TCS CogaLex VI submission

This is a description of our system submitted to the CogaLex VI shared task.
The labeled test sets can be found in the folder “annotated test sets”. The "models" folder contains the trained models that were used for the final annotation.

### TODO - Voting

### XLM-RoBERTa 

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


### Contrast Maps 
In order to improve the accuracy of the prediction provided by the XLM-RoBERTa based subsystem, we added a voting system to our pipeline, which makes use of the concept of Contrast Maps as shown in [3]. The approach introduced by Samenko et al. [3] aims to further distinguish synonyms from antonyms using only information already present in word embeddings.
To enable a multilingual and light-weight model, we adapted the system to use mBPEmb [4] as word embeddings for training and inference. This enabled us to train the several models in three languages, improving accuracy for less performant and hitherto unseen languages.
From the range of architectures proposed by Samenko et al. [3] and available from [5], the Siamese network performed best with the following hyperparameter:  
-	Optimizer: Adam
-	Learning rate: 1e-5
-	Epochs: 900 / 150
-	Loss function: cross entropy
The model was first trained on all CogaLex VI training data in all languages simultaneously for 900 epochs followed by 150 epochs with Chinese training data only based on the informed assumption that it represents the most high-quality dataset from the repository. 


### References
[1] Conneau, A., Khandelwal, K., Goyal, N., Chaudhary, V., Wenzek, G., Guzmán, F., ... & Stoyanov, V. (2019). Unsupervised cross-lingual representation learning at scale. arXiv preprint arXiv:1911.02116.

[2] Wolf, T., Debut, L., Sanh, V., Chaumond, J., Delangue, C., Moi, A., ... & Brew, J. (2019). HuggingFace's Transformers: State-of-the-art Natural Language Processing. ArXiv, arXiv-1910.

[3] Samenko, I., Tikhonov, A., & Yamshchikov, I. P. 2020. Synonyms and Antonyms: Embedded Conflict. ArXiv:2004.12835v1 [Cs]. Retrieved from http://arxiv.org/abs/2004.12835v1

[4] Heinzerling, B., & Strube, M. 2019. BPEMB: Tokenization-free pre-trained subword embeddings in 275 languages. LREC 2018 - 11th International Conference on Language Resources and Evaluation, 2989–2993. Retrieved from https://nlp.h-its.org/bpemb/#multibpemb

[5] https://github.com/i-samenko/Triplet-net
