# ShopSmart Data Warehouse Project

## Introduction aux entrepôts de données

### Pourquoi une entreprise aurait besoin d’un entrepôt de données ?

Les **bases opérationnelles (OLTP)** gèrent les opérations quotidiennes (ventes, commandes, stocks).
Elles ne sont **pas conçues pour l’analyse stratégique**.
L’**entrepôt de données (OLAP)** permet de :

* Centraliser les données provenant de plusieurs sources (CRM, ERP, site e-commerce).
* Historiser les informations pour le suivi dans le temps.
* Améliorer la qualité et la cohérence des données.
* Permettre des **analyses complexes et rapides** (tableaux de bord, BI).

**→ OLTP = opérations | OLAP = analyses.**

---

## Comparaison OLTP vs OLAP

| Critère   | OLTP                         | OLAP                               |
| --------- | ---------------------------- | ---------------------------------- |
| Objectif  | Enregistrer les transactions | Analyser les données               |
| Données   | Détail, en temps réel        | Historique, consolidé              |
| Structure | Tables normalisées           | Schéma en étoile ou flocon         |
| Requêtes  | Courtes, fréquentes          | Lentes, agrégées                   |
| Exemple   | Système de commandes Amazon  | Tableau de bord de ventes Power BI |

---

## Concepts clés

* **Entrepôt de données (DW)** : Base centrale pour les analyses.
* **KPI (Indicateur clé de performance)** : Mesure pour suivre les objectifs (CA, panier moyen, fidélisation…).
* **Modèle en étoile / flocon** : Organisation des tables (faits + dimensions).

---

## Environnement technique

| Outil                         | Rôle                                      |
| ----------------------------- | ----------------------------------------- |
| **PhpMyAdmin / XAMPP / WAMP** | Gestion de la base MySQL                  |
| **Power BI**                  | Visualisation et tableaux de bord         |
| **GitHub**                    | Documentation et versionnage              |
| **SQL / ETL / ELT**           | Intégration et transformation des données |

---

## Architecture : Approches

| Approche                | Description                           |
| ----------------------- | ------------------------------------- |
| **Inmon (top-down)**    | Entrepôt central puis Data Marts      |
| **Kimball (bottom-up)** | Data Marts intégrés dans un DW global |
| **Data Vault**          | Flexible, orientée historisation      |

---

## Stockage et Cloud

| Type               | Description                                 |
| ------------------ | ------------------------------------------- |
| **DW On-premise**  | Géré localement (Oracle, SQL Server)        |
| **DW Cloud**       | Externalisé (BigQuery, Snowflake, Redshift) |
| **Format Parquet** | Colonnaire, compressé, optimisé Big Data    |

---

## ETL vs ELT

| Étape         | ETL                                | ELT                             |
| ------------- | ---------------------------------- | ------------------------------- |
| **Extract**   | Extraction des données             | Extraction des données          |
| **Transform** | Transformation avant le chargement | Transformation après chargement |
| **Load**      | Chargement dans DW                 | Chargement brut dans DW         |
| **Exemples**  | Talend, SSIS                       | Snowflake, BigQuery             |

**Pipeline de données = chemin complet de la donnée (source → analyse).**

---

## Exemple SQL – Création de tables

```sql
CREATE TABLE customers (
    customer_id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(150),
    country VARCHAR(50),
    signup_date DATE
);

CREATE TABLE products (
    product_id SERIAL PRIMARY KEY,
    product_name VARCHAR(100),
    category VARCHAR(50),
    price DECIMAL(10,2)
);
```

---

## Exemple SQL – Transformation (ETL)

```sql
-- Jointure pour créer une table de faits complète
CREATE TABLE fact_orders AS
SELECT 
    o.order_id,
    c.customer_id,
    p.product_id,
    oi.quantity,
    oi.unit_price,
    (oi.quantity * oi.unit_price) AS total_amount,
    o.order_date
FROM orders o
JOIN customers c ON o.customer_id = c.customer_id
JOIN order_items oi ON o.order_id = oi.order_id
JOIN products p ON oi.product_id = p.product_id;
```

---

## KPIs principaux

| Indicateur               | Formule                                      | Objectif                      |
| ------------------------ | -------------------------------------------- | ----------------------------- |
| **CA mensuel**           | `SUM(total_amount)`                          | Mesurer les ventes            |
| **Panier moyen**         | `SUM(total_amount)/COUNT(DISTINCT order_id)` | Évaluer la valeur moyenne     |
| **Taux de fidélisation** | `(Clients récurrents / Clients totaux)`      | Identifier la fidélité        |
| **Top produits**         | `ORDER BY SUM(quantity)`                     | Trouver les meilleures ventes |

---

## Sécurité par rôles

```sql
CREATE ROLE analyst;
GRANT SELECT ON ALL TABLES IN SCHEMA public TO analyst;

CREATE ROLE manager;
GRANT SELECT, INSERT, UPDATE ON ALL TABLES IN SCHEMA public TO manager;
```

---

## Power BI – Tableaux de bord

* **Page 1 :** Vue globale (CA, panier moyen, top produits)
* **Page 2 :** Fidélisation client et taux de réachat
* **Page 3 :** Analyse par période (évolution mensuelle)

---

## Méthodologie P.A.C.E

| Étape              | Objectif                             | Exemple                           |
| ------------------ | ------------------------------------ | --------------------------------- |
| **P – Planifier**  | Identifier les besoins métiers       | Ex : besoin d’un suivi des ventes |
| **A – Analyser**   | Nettoyer et structurer les données   | SQL, ETL                          |
| **C – Construire** | Créer tables, KPIs, modèles Power BI | Schéma en étoile                  |
| **E – Exécuter**   | Déployer et analyser les résultats   | Dashboard Power BI                |

