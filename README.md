# RNE Explorer 🏛️

Une application web ultra-rapide et légère pour explorer le **Registre National des Entreprises (RNE)** français, directement dans votre navigateur.

[![Github Pages](https://img.shields.io/badge/Deploy-GitHub%20Pages-blue?style=flat-square&logo=github)](https://bizouarn.github.io/RneDemo/)
[![DuckDB](https://img.shields.io/badge/Powered%20by-DuckDB--Wasm-orange?style=flat-square)](https://duckdb.org/docs/api/wasm/overview)

## 🚀 Concept

Ce projet démontre comment interroger des jeux de données massifs (plusieurs gigaoctets) de manière fluide sans serveur backend complexe. L'intégralité de la logique de recherche et du traitement des données s'exécute côté client.

### Points clés :
- **Zero Backend** : Pas d'API, pas de base de données SQL distante. Tout est statique.
- **DuckDB-Wasm** : Utilisation du moteur analytique DuckDB compilé en WebAssembly pour des performances de pointe.
- **Format Parquet** : Les données sont stockées au format Apache Parquet, permettant des lectures colonnaires optimisées via HTTP (Range Requests).
- **Interface Moderne** : Une UI épurée conçue pour la rapidité et la clarté.

## 🛠️ Stack Technique

- **Frontend** : HTML5, CSS3 (Vanilla), JavaScript (ES Modules).
- **Moteur de données** : [DuckDB-Wasm](https://duckdb.org/docs/api/wasm/overview).
- **Stockage des données** : Fichiers `.parquet` compressés et optimisés.
- **Gestion des fichiers volumineux** : [Git LFS](https://git-lfs.github.com/) pour le versionnement des données.
- **Déploiement** : GitHub Pages via GitHub Actions.

## 📂 Structure du projet

```text
.
├── .github/workflows/  # Workflow de déploiement automatique
├── example/
│   ├── index.html      # Application principale (UI + Logique DuckDB)
│   ├── unites_legales.parquet    # Données des unités légales (~1.5 Go)
│   └── etablissements.parquet     # Données des établissements
└── .gitattributes      # Configuration Git LFS
```

## 📋 Utilisation

L'outil permet d'effectuer des recherches sur plusieurs critères :
1. **Nom de l'entreprise** : Recherche textuelle sur la dénomination.
2. **SIREN (9 chiffres)** : Accès direct à la fiche de l'unité légale.
3. **SIRET (14 chiffres)** : Recherche d'un établissement spécifique.

## ⚙️ Installation locale

Pour faire tourner le projet localement, vous aurez besoin d'un serveur HTTP simple (car DuckDB-Wasm nécessite des headers COOP/COEP pour de meilleures performances, bien qu'il puisse fonctionner sans en mode dégradé).

1. **Cloner le dépôt** (assurez-vous d'avoir Git LFS installé) :
   ```bash
   git clone https://github.com/bizouarn/RneDemo.git
   cd RneDemo
   ```

2. **Lancer un serveur local** (exemple avec Python) :
   ```bash
   python -m http.server 8000
   ```
   *Note : Pour une expérience optimale, utilisez un serveur supportant les SharedArrayBuffer.*

3. **Ouvrir `http://localhost:8000/example/`** dans votre navigateur.

## 📊 Données

Les données proviennent de l'INSEE et de l'INPI (via le RNE). Les fichiers Parquet sont générés à partir des exports officiels et structurés pour minimiser le volume de données transféré lors des recherches.

---
*Projet réalisé à des fins de démonstration technique sur l'utilisation de DuckDB-Wasm avec des fichiers Parquet volumineux.*
