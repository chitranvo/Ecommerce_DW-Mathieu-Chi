# Ecommerce_DW-Mathieu-Chi

# 🧠 Introduction aux Entrepôts de Données

## 🔐 Informations générales

* **Outils utilisés :** PhpMyAdmin, Power BI, XAMPP/WAMP, DBT, Git
* **Méthodologie :** P.A.C.E — *Planifier, Analyser, Construire, Exécuter*

---

## 📘 1. Pourquoi un entrepôt de données ?

Les bases **opérationnelles (OLTP)** gèrent les transactions quotidiennes (ventes, commandes, stocks, factures).
Elles sont optimisées pour la rapidité d’exécution, mais **ne suffisent pas pour l’analyse stratégique**.

L’**entrepôt de données (OLAP)** permet de :

* Centraliser les données issues de plusieurs sources (CRM, ERP, e-commerce, etc.)
* Historiser les données sur plusieurs années
* Nettoyer et homogénéiser les informations
* Analyser les tendances à travers des tableaux de bord (BI)

👉 En résumé : **OLTP = gestion quotidienne**, **OLAP = décision stratégique**

---

## ⚖️ 2. Différence entre Transactions et Analyses

| **Aspect**        | **OLTP (Transactions)** | **OLAP (Analyses)**                 |
| ----------------- | ----------------------- | ----------------------------------- |
| Objectif          | Gérer les opérations    | Prendre des décisions               |
| Type d’opérations | Petites, fréquentes     | Requêtes complexes                  |
| Données           | Actuelles, détaillées   | Historiques, agrégées               |
| Structure         | Tables normalisées      | Schéma étoile / flocon              |
| Exemple           | Commande Amazon         | Tableau de bord ventes 2024 vs 2025 |

---

## 🎯 3. Point de vue marketing

Si j’étais **directeur marketing**, j’aurais besoin de :

* **CA mensuel**
* **Taux de réachat / fidélisation**
* **Panier moyen**
* **Top produits / catégories**
* **Meilleures localisations clients (Best_loc)**

Ces **KPIs** aident à évaluer la performance commerciale et à ajuster la stratégie.

---

## 🧩 4. Concepts et définitions

| **Terme**                  | **Définition**                                    |
| -------------------------- | ------------------------------------------------- |
| **DW (Data Warehouse)**    | Base de données dédiée à l’analyse                |
| **OLTP**                   | Système transactionnel (exécution des opérations) |
| **OLAP**                   | Système analytique (aide à la décision)           |
| **KPI**                    | Indicateur clé de performance                     |
| **Schéma étoile / flocon** | Structure logique d’un entrepôt de données        |

---

## 🏗️ 5. Modèles et architectures

### Approches :

* **Inmon (Top-down)** : entrepôt central → data marts
* **Kimball (Bottom-up)** : data marts → entrepôt global
* **Data Vault** : approche flexible, centrée sur l’historisation

### Notions importantes :

* **Grain** : niveau de détail des données d’une table de faits
* **Clé technique** : identifiant stable, indépendant de la clé métier
* **Dimension conforme** : dimension partagée entre plusieurs data marts

---

## ☁️ 6. Infrastructures et formats

| **Type**            | **Exemple**                   | **Avantage principal**      |
| ------------------- | ----------------------------- | --------------------------- |
| DW on-premise       | Oracle, SQL Server            | Contrôle interne            |
| DW cloud            | Snowflake, BigQuery, Redshift | Scalabilité, flexibilité    |
| Format CSV          | Texte brut, simple            | Facile à manipuler          |
| Format Parquet/ORC  | Format binaire compressé      | Efficace pour le Big Data   |
| Stockage colonnaire | Par colonne                   | Lecture rapide et sélective |
| Partitionnement     | Par date, région...           | Performance accrue          |

---

## 🔄 7. Intégration et transformation des données (ETL / ELT)

### 🔹 **ETL (Extract – Transform – Load)**

1. Extraction des sources (BDD, fichiers, API)
2. Transformation (nettoyage, normalisation)
3. Chargement dans l’entrepôt

🧰 Exemple : Talend, Informatica, SSIS
💡 Adapté aux systèmes traditionnels.

### 🔹 **ELT (Extract – Load – Transform)**

1. Extraction des données sources
2. Chargement brut dans le DW
3. Transformation dans le moteur du DW (SQL, Spark, BigQuery...)

⚡ Adapté aux environnements **Cloud / Big Data**
🧰 Exemple : Snowflake, BigQuery, Redshift

---

## 🔁 8. Pipeline de données

Un **pipeline** correspond au **chemin de transformation des données**, depuis leur extraction jusqu’à leur visualisation finale (ETL/ELT → DW → Power BI).

---

## 🧮 9. DBT et gestion des données

### Pourquoi séparer données brutes et transformées ?

* Pour assurer **traçabilité, qualité et reproductibilité** des transformations.

### DBT apporte :

* Gestion versionnée des modèles SQL
* Tests automatiques
* Documentation intégrée
* Automatisation des flux de transformation

---

## 🔐 10. Sécurité par rôles

* Attribution de **droits d’accès** selon le rôle utilisateur
* Protection des données sensibles (ex : clients, ventes)

---

## 📊 11. Indicateurs (KPIs)

* **CA (Chiffre d’affaires)**
* **Top produits**
* **Panier moyen**
* **Top catégories**
* **Taux de fidélisation**
* **Best location**
* **Inscription moyenne**

---

## 💻 12. Environnement de développement

* **Base :** PostgreSQL
* **Outils :** PhpMyAdmin, Power BI
* **Modélisation :** Schéma en étoile
* **Sécurité :** Rôles utilisateurs
* **Versionning :** GitHub

---

## 🧾 13. Présentation finale

* **README Git** (documentation complète du projet)
* **Résumé exécutif** (synthèse des résultats et KPIs clés)
* **Tableau de bord Power BI** (analyse visuelle des ventes et clients)

---

## 🚀 Méthodologie P.A.C.E

| **Étape**          | **Description**                                       |
| ------------------ | ----------------------------------------------------- |
| **P – Planifier**  | Identifier les besoins et les sources de données      |
| **A – Analyser**   | Nettoyer, transformer et modéliser les données        |
| **C – Construire** | Mettre en place le Data Warehouse et les KPIs         |
| **E – Exécuter**   | Créer les visualisations et les rapports décisionnels |

---

Souhaites-tu que je te fasse aussi la **version courte du README** (résumé exécutif, 8–10 lignes) pour la fin de ton dépôt GitHub ?
