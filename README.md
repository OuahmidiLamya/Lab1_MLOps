# Lab 1 : Du notebook au mini-système production-ready

## **Étape 1 : Initialiser la structure du projet**

La structuration du projet a commencé par la création d’un dossier principal nommé `mlops-lab-01`. À l’intérieur, plusieurs sous-dossiers ont été créés pour organiser les données, les modèles, le code source, les logs et le registry. Un fichier `current_model.txt` a également été ajouté dans le dossier `registry`. La structure du projet a ensuite été vérifiée à l’aide de la commande permettant d’afficher l’arborescence.

<img width="1919" height="916" alt="image" src="https://github.com/user-attachments/assets/de2c844e-ff75-4123-9d38-a427b8d900de" />

## **Étape 2 : Préparer l'environnement Python**

La préparation de l’environnement Python a commencé par la création d’un environnement virtuel nommé `venv_mlops`, puis son activation. Ensuite, l’outil `pip` a été mis à jour afin d’utiliser la version la plus récente. Enfin, les bibliothèques nécessaires au projet ont été installées, notamment `pandas`, `numpy`, `scikit-learn`, `fastapi`, `uvicorn` et `joblib`.

<img width="1728" height="919" alt="image" src="https://github.com/user-attachments/assets/a90276a5-a222-4719-9151-bb4c45242adc" />

## **Étape 3 : Générer le dataset**

La génération du dataset a été réalisée à l’aide d’un script Python nommé `generate_data.py`. Ce script a permis de créer un jeu de données synthétique contenant des informations liées aux clients, telles que l’ancienneté, le nombre de plaintes, la durée moyenne de session, le type d’abonnement, la région et la variable cible `churn`. Après l’exécution du script, un fichier `raw.csv` contenant 1200 lignes a été généré et stocké dans le dossier `data`.

<img width="1440" height="276" alt="image" src="https://github.com/user-attachments/assets/6037077f-12d7-4723-b8c0-434e2fe5cc94" />

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/0954cfb1-a4c2-448d-8dd6-d53c1a62343f" />

## **Étape 4 : Préparer les données + quality checks**

La préparation des données a été réalisée à l’aide du script `prepare_data.py`. Les données brutes ont été chargées à partir du fichier `raw.csv`, puis nettoyées à travers différentes transformations. Des contrôles de qualité ont ensuite été appliqués afin de vérifier la structure des données et la cohérence des valeurs. À l’issue de cette étape, un fichier `processed.csv` a été généré dans le dossier `data`, ainsi qu’un fichier `train_stats.json` contenant les statistiques des variables numériques dans le dossier `registry`.

<img width="1725" height="194" alt="image" src="https://github.com/user-attachments/assets/92e3beea-7577-497e-89b7-7ce99e289da1" />

<img width="1915" height="1079" alt="image" src="https://github.com/user-attachments/assets/73e759b2-d18c-470d-99ac-c4a9e3a538fd" />

<img width="683" height="532" alt="image" src="https://github.com/user-attachments/assets/d7e6c27a-4e76-48e4-a36e-91e5c03c6e96" />

## **Étape 5 : Entraîner, versionner et valider le modèle**

L’entraînement du modèle a été effectué à l’aide du script `train.py`. Les données prétraitées ont été chargées depuis le fichier `processed.csv`, puis séparées en variables explicatives et variable cible. Un pipeline de traitement et de modélisation a ensuite été entraîné et évalué à l’aide de plusieurs métriques. Le modèle obtenu a été sauvegardé dans le dossier `models` avec un identifiant de version, et les informations associées à l’entraînement ont été enregistrées dans le registry. Le modèle n’a pas été validé pour le déploiement, car il n’a pas passé le seuil de validation défini.

<img width="1888" height="366" alt="image" src="https://github.com/user-attachments/assets/6013d6f1-eafd-4586-b8a0-c4d84f3d36aa" />

## **Étape 6 : Inspecter la registry et le modèle courant**

L’inspection de la registry et du modèle courant a été réalisée à l’aide du script `evaluate.py`. Les données prétraitées ont été utilisées pour entraîner et évaluer un modèle avec un ajustement du seuil de décision afin d’optimiser la métrique F1. Les performances du modèle ont été calculées, puis comparées à une baseline. Le modèle entraîné a été sauvegardé dans le dossier `models`, et les métadonnées associées ont été enregistrées dans la registry. Le modèle validé a ensuite été défini comme modèle courant dans le fichier `current_model.txt`.

<img width="1893" height="432" alt="image" src="https://github.com/user-attachments/assets/086d0c1e-8bcb-4f15-b731-746e92350f64" />

## **Étape 7 : Créer une API /predict qui utilise le modèle courant**

La création de l’API a permis de mettre en place un service FastAPI exposant le modèle courant. Un endpoint `/health` a été ajouté pour vérifier l’état de l’API, ainsi qu’un endpoint `/predict` pour effectuer des prédictions de churn à partir des données fournies. Le modèle utilisé est chargé dynamiquement depuis le registry et chaque prédiction est enregistrée dans un log.

<img width="1848" height="435" alt="image" src="https://github.com/user-attachments/assets/8e665aee-b3d3-40f5-96f2-a377d4bf3f48" />

<img width="1919" height="702" alt="image" src="https://github.com/user-attachments/assets/d4f1209a-8448-4c68-93c8-ed9b5fdea9dc" />

<img width="1919" height="776" alt="image" src="https://github.com/user-attachments/assets/f00727b4-a191-44c3-99ff-f75592d40daf" />

<img width="936" height="815" alt="image" src="https://github.com/user-attachments/assets/a7cccb23-cda5-44eb-8780-4e3bcaa8e468" />

<img width="1235" height="846" alt="image" src="https://github.com/user-attachments/assets/9733e592-672a-448c-be4f-b630a4783d54" />

<img width="835" height="879" alt="image" src="https://github.com/user-attachments/assets/102ac424-59dd-4578-89e1-dbb2a46c1db0" />

<img width="1252" height="863" alt="image" src="https://github.com/user-attachments/assets/70b54f20-ff44-49f1-9ed9-229ee3222557" />

<img width="812" height="844" alt="image" src="https://github.com/user-attachments/assets/40f16686-1043-4033-980f-a7e0b1153fae" />

<img width="1241" height="860" alt="image" src="https://github.com/user-attachments/assets/6e082a41-9a77-4f8c-b943-6ec83d4da380" />

<img width="888" height="918" alt="image" src="https://github.com/user-attachments/assets/7265249f-24c3-49d2-adf1-d97ab60d6e22" />

## **Étape 8 : Détecter une dérive des données via les logs**

La détection de dérive des données a été réalisée à partir des logs de prédiction. Les statistiques issues de l’entraînement ont été comparées aux données récentes observées en production en calculant un score de dérive pour chaque variable numérique. Une alerte est affichée lorsqu’un écart significatif est détecté, indiquant qu’une analyse complémentaire ou un réentraînement du modèle peut être envisaé.

<img width="1913" height="297" alt="image" src="https://github.com/user-attachments/assets/1b1748f4-ec61-437d-865f-8181b8ec7ed5" />

## **Étape 9 : Gérer les versions du modèle et revenir en arrière**

La gestion des versions du modèle a été assurée à l’aide d’un script de registry permettant d’enregistrer, lister et activer différentes versions du modèle. Chaque modèle entraîné est sauvegardé avec ses métadonnées et peut être défini comme modèle courant ou remplacé par une version antérieure en cas de besoin. Le mécanisme de retour arrière permet ainsi de restaurer automatiquement une version stable du modèle. Cette opération met à jour le fichier *current_model.txt*, garantissant que l’API utilise immédiatement la version sélectionnée, tout en assurant la traçabilité et la fiabilité du déploiement en production.

<img width="1906" height="518" alt="image" src="https://github.com/user-attachments/assets/7a6e167f-c645-427e-8660-83826a739c0b" />
