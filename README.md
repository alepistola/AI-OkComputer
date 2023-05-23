# Artificial Intelligence Project - Interpretable Academic Dropout

## Description of the problem
The problem of academic dropout concerns students who do not complete their studies. This is a problem because such dropouts can cause high costs and make society less productive.  In order to help students not to drop out of studies, efforts are being made to develop an artificial intelligence system that can predict the risk of dropout and then go on to propose personalised solutions. All this, with the aim of helping students complete their studies by improving their success rate.
However, the 'black box' nature of machine learning systems does not allow for an understanding of the system's decision-making process.
This represents a problem as it can give rise to uncertainty and mistrust of the prediction especially when the field of application is a critical one or the decision concerns an ethically sensitive area.
Furthermore, the lack of interpretability makes the debugging process and the identification of possible biases in the model difficult.
For these reasons, the main focus of the following project is the development of a machine learning system and the use of interpretation techniques in order to guarantee transparency in the decision-making process of the proposed system.

## Proposed solution
The proposed solution is a solution resulting from a development process comprising data pre-processing operations, search for the optimal model, hyperparameter tuning of the model itself and local and global interpretation operations.  
For the project development, it has been used a pseudonymised dataset provided by the University of Bologna including information on students and corresponding taken exams.  
The presence of sensitive information such as gender or economic status made it very important and meaningful to interpret the results obtained in order to ascertain whether or not the model discriminated on the basis of these attributes.  
The proposed solution, in conclusion, is a jupyter notebook comprising all development stages. The final model chosen for interpretation is an Extreme Gradient Boosting (xgb).

## Results
Performance is calculated through the metrics of **Accuracy** and **ROC-AUC** score. 
The models shown in the diagram refer to the best 4:

![Best 4 models accuracy](/readmeAssets/accuracy_4.png "Accuracy per i migliori 4 modelli")
![Best 4 models roc-auc score](/readmeAssets/roc_auc_4.png "ROC-AUC per i migliori 4 modelli")

Below are the confusion matrices of the 2 best models (RF, XGBoost):

![XGBoost confusion matrix](/readmeAssets/confmat_xgboost.png "Matrice di confusione per XGBoost")
![RF confusion matrix](/readmeAssets/confmat_rf.png "Matrice di confusione per RF")

## SMOTE + UnderSampling XGBoost
As the next design configuration, it was planned to use SMOTE and UnderSampling techniques in concatenation in order to obtain a balanced dataset.

![Confusion matrix for XGBoost + smote + undersampling](/readmeAssets/xgboost_smote.png "Matrice di confusione per XGBoost + smote + undersampling")

**Accuracy**: 0.91
**Recall**: 0.90
**ROC-AUC**: 0.89


## Conclusion and discussion of results
In the end, data pre-processing procedures were applied to the datasets provided by the University of Bologna and the type of model capable of obtaining the best performance on binary classification problems with unbalanced multi-dimensional datasets was researched.  
Having chosen the optimal model, XGBoost, we proceeded to perform hyper-parameter tuning through the GridSearchCV library. In order to achieve better performance, the SMOTE and UnderSampling techniques were concatenated to balance the dataset, resulting in a model that could achieve considerable performance (Accuracy: 0.91, Recall: 0.90, ROC-AUC: 0.89).  
At this point, various interpretability techniques were successfully applied (Feature Importance, PDP, Feature Interaction, Glassbox, LIME and Global surrogate models) with the aim of increasing the interpretability and reliability of the model itself by trying to identify whether bugs or biases were present in the classification process.  
If the InterpretML models guarantee the analyst's interpretation and understanding, the model proposed in this project (using Molnar's algorithm) is approximated by an EBM model with an approximation of 98%, so it can be defined as highly interpretable without any problems. In conclusion, the objectives of the project can be considered to have been achieved.
