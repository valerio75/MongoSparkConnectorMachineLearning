
# Esempio di machine learnig supervisionato utilizzando MongoDB ed Apache Spark
# L'esempio è stato presentato durante il Meetup di Deep Learning Italia del 11/11/2019 - Roma

## Author Info
Valerio Morfino [Linkedin page](https://www.linkedin.com/in/valerio-morfino/)

## Descrizione
Il codice contiene un esempio di Machine Learning supervisionato per la rilevazione di un attasso SYN-DOS.
Il dataset è costituito da rilevazioni statistiche estratte da un feature extractor realtive a pacchetti IP relativi a device IOT. Le feature rappresentano delle statistiche relative allo stato implicito del canale. Per maggiori informazioni sul dataset si faccia riferimento al link: https://arxiv.org/pdf/1802.09089.pdf
Il dataset è costituito da: 11000 sample (10000 normal + 1000 attack). Ogni sample è composto da 115 feature double + 1 classe di tipo stringa.
La versione completa del dataset è reperibile al link: https://drive.google.com/drive/folders/1kmoWY4poGWfmmVSdSu-r_3Vo84Tu4PyE

## Prerequisiti
Per replicare l'esempio presentato è necessario:
- Un account Databricks community edition,  che può essere creato al seguente link: https://databricks.com/signup#signup/community
- Un account MongoDB Atlas che può essere creato al seguente link: https://www.mongodb.com/cloud/atlas/lp/general/try

## Contenuto
- dataset.zip, dataset 
- SYNDOS-WRITE-TO-MONGO.ipynb, notebook da importare su Databricks che legge il file csv e crea la collection in MongoDB
- SYNDOS-TRAINING.ipynb, notebook da importare su Databricks che effettua il training leggendo i dati da MongoDB

# Istruzioni
Creare gli account su Databricks e MongoDB Atlas.

## Configurazione di MongoDB Atlas
Scompattare il file dataset.zip ed importare i file dataset in DBFS seguendo le istruzioni: https://docs.databricks.com/user-guide/importing-data.html

## Preparazione dell'ambiente Databricks
Importare i file SYNDOS-WRITE-TO-MONGO.ipynb e SYNDOS-TRAINING.ipynb su Databricks seguendo le istruzioni: https://docs.databricks.com/user-guide/notebooks/notebook-manage.html
Creare un nuovo cluster seguendo le istruzioni: https://docs.databricks.com/user-guide/clusters/create.html
Accedere alla sezione "Libraries" della configurazione del cluster ed installare il MongoDBSpark connector importanto il riferimento maven: org.mongodb.spark:mongo-spark-connector_2.11:2.4.1

### Creazione collection su MongoDB da Spark
Aprire il Notebook SYNDOS-WRITE-TO-MONGO.ipynb e modificare la variabile MONGO_URI inserendo l'URI prelevato da MongoDB Atlas.
Eseguire il Notebook e verificare su Atlas che la collezione sia stata correttamente creata

### Training
Aprire il Notebook SYNDOS-TRAINING.ipynb e modificare la variabile MONGO_URI inserendo l'URI prelevato da MongoDB Atlas.
Eseguire il Notebook


