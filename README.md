# TP 31 : Architecture Microservices avec RabbitMQ

## 📡 Aperçu
Ce projet illustre une communication asynchrone entre deux microservices **Spring Boot** via le broker de messages **RabbitMQ**.

## 🏗️ Architecture

### 1. Producer Service (`RabbitMQ Producer`)
- Expose une API REST (`POST /api/produce`).
- Reçoit un objet JSON (User) avec `publicId` et `fullName`.
- Publie le message sur un **Exchange** RabbitMQ.

### 2. RabbitMQ Server
- Agit comme intermédiaire (Message Broker).
- Supporte le découplage temporel entre le producteur et le consommateur.

### 3. Consumer Service (`RabbitMQ Consumer`)
- Écoute une **Queue** spécifique.
- Désérialise le message JSON.
- Persiste les données reçues dans une base **MySQL**.

## 🚀 Démarrage

1.  **Pré-requis** :
    - RabbitMQ (Port 5672/15672)
    - MySQL (Port 3306)

2.  **Lancer le Producer** :
    ```bash
    cd microservices-messaging-producer
    mvn spring-boot:run
    ```

3.  **Lancer le Consumer** :
    ```bash
    cd microservices-messaging-consumer
    mvn spring-boot:run
    ```

## 📩 Test
Envoyer une requête POST :
```json
{
  "publicId": "UID-101",
  "fullName": "Alice Wonderland"
}
```
Vérifier les logs du Consumer pour confirmer la réception et la sauvegarde.
