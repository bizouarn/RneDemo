# RNE Explorer 🏛️

Application web légère pour explorer le **Registre National des Entreprises (RNE)** français dans le navigateur.

[![Github Pages](https://img.shields.io/badge/Deploy-GitHub%20Pages-blue?style=flat-square&logo=github)](https://bizouarn.github.io/RneDemo/)
[![DuckDB](https://img.shields.io/badge/Powered%20by-DuckDB--Wasm-orange?style=flat-square)](https://duckdb.org/docs/api/wasm/overview)

## 🚀 Concept

Interrogation de jeux de données massifs sans serveur. Toute la logique s'exécute côté client.

### Points clés :
- **Zero Backend** : Tout est statique.
- **DuckDB-Wasm** : Moteur analytique WebAssembly.
- **Format Parquet** : Lectures colonnaires via HTTP.
- **Interface Moderne** : UI épurée et claire.

## 🛠️ Stack Technique

- **Frontend** : HTML5, CSS3, JS.
- **Moteur** : [DuckDB-Wasm](https://duckdb.org/docs/api/wasm/overview).
- **Stockage** : Fichiers `.parquet`.
- **Fichiers volumineux** : [Git LFS](https://git-lfs.github.com/).
- **Déploiement** : GitHub Pages.

## 📂 Structure

```text
.
├── .github/workflows/  # Déploiement
├── _site/
│   ├── index.html      # Application
│   ├── unites_legales.parquet    # ~290 Mo
│   └── etablissements.parquet    # ~415 Mo
└── .gitattributes      # LFS
```

## 📋 Utilisation

Recherche par :
1. **Nom** : Dénomination.
2. **SIREN** : Unité légale.
3. **SIRET** : Établissement.

## ⚙️ Installation

1. **Cloner** :
   ```bash
   git clone https://github.com/bizouarn/RneDemo.git
   cd RneDemo
   ```
2. **Serveur** :
   ```bash
   python -m http.server 8000
   ```
3. **Ouvrir** `http://localhost:8000/_site/`.

## 📊 Données

Source INSEE/INPI. Démo avec jeu de données réduit (entreprises actives).

---
*Démonstration : DuckDB-Wasm + Parquet.*
