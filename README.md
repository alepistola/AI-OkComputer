# Progetto Intelligenza artificiale  Interpretable Dropout (Dropout  accademico)

Corso di Laurea Magistrale in Informatica  
Anno Accademico 2022-2023  
Gruppo:  OkComputer  
Alessandro Pistola (1058248)

## Descrizione del problema
Il problema del dropout accademico riguarda gli studenti che non completano gli studi. Questo rappresenta un problema poichè tale abbandono può causare costi elevati e rendere la società meno produttiva.  Al fine di aiutare gli studenti a non abbandonare gli studi, si sta cercando di sviluppare un sistema di intelligenza artificiale che possa prevedere il rischio di dropout per poi andare a proporre soluzioni personalizzate. Tutto questo, con l’obiettivo di aiutare gli studenti a completare gli studi migliorandone il tasso di successo.
La natura ”black box” dei sistemi di machine learning non permette però di comprendere il processo di decision making del sistema.
Ciò rappresenta un problema poichè può suscitare incertezza e diffidenza nei confronti della predizione soprattutto quando il campo di applicazione è un settore critico o la decisione riguarda un ambito eticamente sensibile.
Inoltre, la mancanza di interpretabilità rende difficile il processo di debugging e l’individuazione di eventuali bias nel modello.
Proprio per queste ragioni, il focus principale del seguente progetto è lo sviluppo di un sistema di machine learning e l’utilizzo di tecniche di interpretabilità al fine di garantire la trasparenza nel processo di decisione del sistema proposto.

## Descrizione della soluzione proposta
La soluzione proposta, è una soluzione nata da un processo di sviluppo comprendente operazioni di preprocessing dei dati, ricerca del modello ottimale, hyperparameter tuning del modello stesso e operazioni di interpretazione locale e globale.  
Per lo sviluppo di tale progetto, si è fatto uso di un dataset pseudonimizzato fornito  dall’Università di Bologna comprendente informazioni relative a studenti e corrispondenti esami sostenuti.  
La presenza di informazioni sensibili come genere o condizione economica ha reso le operazioni di interpretazione dei risultati ottenuti molto importanti e sensate, al fine di constatare se il modello discriminasse o meno sulla base di tali attributi.  
La soluzione proposta, in conclusione, è un notebook jupyter comprendente tutte le fasi di sviluppo. Il modello finale scelto per l’interpretazione è un Extreme Gradient Boosting (xgb).

## Risultati
Le perfomance vengono calcolate attraverso le metriche di **Accuracy** e punteggio **ROC-AUC**. 
I modelli riportati nello schema fanno riferimento ai migliori 4:

![Accuracy per i migliori 4 modelli](/readmeAssets/accuracy_4.png "Accuracy per i migliori 4 modelli")
![Roc-auc score per i migliori 4 modelli](/readmeAssets/roc_auc_4.png "ROC-AUC per i migliori 4 modelli")
Di seguito sono riportate invece le matrici di confusione dei 2 modelli migliori (RF, XGBoost):

![Matrice di confusione per XGBoost](/readmeAssets/confmat_xgboost.png "Matrice di confusione per XGBoost")
![Matrice di confusione per RF](/readmeAssets/confmat_rf.png "Matrice di confusione per RF")

## SMOTE + UnderSampling XGBoost
Come successiva configurazione progettuale, si `e pensato di utilizzare le tecniche di SMOTE e UnderSampling in concatenazione al fine di ottenere un dataset bilanciato.

![Matrice di confusione per XGBoost + smote + undersampling](/readmeAssets/xgboost_smote.png "Matrice di confusione per XGBoost + smote + undersampling")

**Accuracy**: 0.91
**Recall**: 0.90
**ROC-AUC**: 0.89

## Conclusione e discussione dei risultati
Riassumendo, sono state applicate delle procedure di data pre-processing ai dataset  forniti dall’Università di Bologna e si è ricercata la tipologia di modello in grado di  ottenere le performance migliori su problemi di classficiazione binaria con dataset  non bilanciato a molte dimensioni.  
Scelto il modello ottimale, XGBoost, si è proceduto effettuando un hyper-parameter  tuning attraverso la libreria GridSearchCV. Al fine di ottenere performance migliori  si sono concatenate le tecniche SMOTE e UnderSampling per bilanciare il dataset,  ottenendo un modello che potesse raggiungere perfomance considerevoli (Accuracy:  0.91, Recall: 0.90, ROC-AUC: 0.89).  
A questo punto sono state applicate con successo varie tecniche di interpretabilità (Feature Importance, PDP, Feature Interaction, modelli Glassbox, LIME e Global  surrogate) con lo scopo di aumentare l’interpretabilità e l’affidabilità del modello  stesso cercando di individuare se presenti bug o bias nel processo di classificazione.  
Se i modelli di InterpretML garantiscono l’interpretazione e la comprensione da  parte dell’analista, il modello che si è proposto in questo progetto (utilizzando  l’algoritmo di Molnar) viene approssimato da un modello EBM con  un’approssimazione del 98%, quindi si pu`o definire, senza problemi, altamente interpretabile. Concludendo, gli obiettivi del progetto possono essere considerati raggiunti.

