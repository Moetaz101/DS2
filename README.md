# 📦 DS1 - Projet CI/CD avec Jenkins

## 🎯 Objectif

Ce projet a pour but de mettre en place un pipeline **CI/CD** avec **Jenkins** pour une application Java/Maven.  
Il intègre également **SonarQube** pour l'analyse de qualité de code, et **Docker** pour la conteneurisation.

---

## 🛠️ Technologies Utilisées

| Outil       | Rôle                                      |
|-------------|-------------------------------------------|
| GitHub      | Stockage et versioning du code source     |
| Jenkins     | Orchestration du pipeline CI/CD           |
| Maven       | Build, gestion des dépendances Java       |
| SonarQube   | Analyse statique de la qualité du code    |
| Docker      | Conteneurisation de l'application         |
| OpenJDK 17  | Environnement d'exécution Java            |

---

## 📂 Structure du Pipeline

```mermaid
graph TD;
  A[GitHub - Push Code] --> B[Jenkins - Clone Repository];
  B --> C[Maven - Build Project];
  C --> D[SonarQube - Analyse Qualité];
  D --> E[Docker - Build Image];
