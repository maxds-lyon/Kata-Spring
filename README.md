[![Ouvrir dans Gitpod](https://gitpod.io/button/open-in-gitpod.svg)](https://gitpod.io/#https://github.com/maxds-lyon/Kata-Spring)
# Kata Bowling en Java Spring Boot

Ce projet est un exemple de Kata Bowling utilisant Java et Spring Boot. Il vous guidera à travers la création d'une application simple pour calculer le score d'un jeu de bowling.

## Prérequis

- Java 17
- Maven
- Un IDE comme IntelliJ IDEA ou Eclipse

## Installation

1. Clonez le dépôt:
   ```bash
   git clone https://github.com/maxds-lyon/Kata-Spring.git
   cd Kata-Spring
   ```

2. Construisez le projet avec Maven:
   ```bash
   mvn clean install
   ```

3. Lancez l'application Spring Boot:
   ```bash
   mvn spring-boot:run
   ```

## Structure du Projet

- `src/main/java/com/max/lyon/kata/`: Contient les classes principales de l'application.
- `src/main/java/com/max/lyon/kata/helloworld/HelloController.java`: Exemple de contrôleur REST.
- `pom.xml`: Fichier de configuration Maven.

## Fonctionnalités

- Calcul du score d'un jeu de bowling.
- API REST pour soumettre les lancers et obtenir le score.

## Endpoints

- `POST /game/new`: Commencer une nouvelle partie.
  - Exemple d'utilisation:
    ```bash
    curl -X POST http://localhost:8080/new
    ```

- `POST /game/{id}/roll`: Soumettre un lancer d'une partie.
  - Exemple d'utilisation:
    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{"pins": 5}' http://localhost:8080/roll
    ```

- `POST /game/{id}/rolls`: Soumettre tous les lancers d'une partie.
  - Exemple d'utilisation:
    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{"rolls": [10, 7, 3, 9, 0, 10, 0, 8, 8, 2, 0, 6, 10, 10, 10, 8, 1]}' http://localhost:8080/rolls
    ```

- `GET /game/{id}/score`: Récupérer le score d'une partie.
  - Exemple d'utilisation:
    ```bash
    curl -X GET http://localhost:8080/score
    ```

## Règles pour calculer le score d'une partie de bowling

1. Une partie de bowling se compose de 10 frames.
2. Dans chaque frame, le joueur a deux lancers pour faire tomber les 10 quilles.
3. Si le joueur fait tomber toutes les quilles avec le premier lancer, c'est un strike. Le score pour cette frame est 10 plus le nombre de quilles abattues dans les deux lancers suivants.
4. Si le joueur fait tomber toutes les quilles en deux lancers, c'est un spare. Le score pour cette frame est 10 plus le nombre de quilles abattues dans le lancer suivant.
5. Si le joueur ne fait pas tomber toutes les quilles en deux lancers, le score pour cette frame est le nombre total de quilles abattues.
6. Le score total de la partie est la somme des scores des 10 frames.
7. Si le joueur réalise un strike ou un spare dans la 10ème frame, il obtient des lancers supplémentaires pour compléter le score de cette frame.