
## The idea

Mysterium clone

-   frontend admin (styrer tilgængelige pakker for alle brugere, kan tilføje nye billeder og temaer)
    
-   frontend ghost (personen der giver kort og starter spillet), players (dem som skal gætte lokation, genstand og karakter)
    
-   backend til kommunikation mellem frontends (socket & room management)
    
-   backend til håndtering af brugere (måske stats?) & billeder og pakker(temaer)
    
-   backend til login
    

Socket for at spille sammen

rooms (room code lavet af ghost)

## Expected DB elements

-   credentials
    

-   stats
    

-   billeder
    
-   temaer
    

  

## Techstack

-   ### Backend
    

-   Node + Sequilize/typeORM (server der håndtere models, api’er)
    
-   Node (socket & room management)
    
-   Node (credentials)
    

-   ### Frontend
    

-   Svelte til admin
    
-   Svelte til brugere(players og ghost)
    

-   ### Database
    

-   PostGree (model data f.eks. stats, temaer)
    
-   MongoDb (user data, credentials)
    

  

## Git strategy

Feature-branching:

1.  You create a new branch from master
    
2.  Develop specific feature until finished
    
3.  Merge feature-branch into master
    

  
  

## Functional requirements

  

### Game functionality

-   A user should be able to create a game/lobby
    
-   A user should be able to join an existing game/lobby
    
-   A lobby should have a user as the lobbymaster (owner rights for the room)
    
-   The application should keep track of the game
    

-   Rounds, phases, turns, progress etc.
    

-   The room should have a chat
    
-   A user should have a personal profile page with stats (?)  
      
    

### User & Authentication functionality

-   A user should be able to login
    

  

### Admin requirements

-   An admin should have access to a separate admin service
    
-   An admin should be able to create and maintain game themes
    
-   An admin should be able to ban players (?)
    
-   An admin should have access to statistics (?)
    
-   An admin should be able to send out global admin messages (chat and/or email?)
    

  

## Non-functional requirements

-   Immutable db (hashing for ID, snapshot and tombstone pattern)
    
-   Idempotence (multiple of same operations gives same result, GUID)
    
-   Location independence (Content Based Addressing)
    
-   Commutativity (independent of the order of messages/events)
    
-   Game-server capable of handling multiple lobbies at once
    

## Project management strategy

-   Asana (Virtual scrumboard)
-   Agile/SCRUMish


## Microservices

[Guide for designing microservices](https://learn.microsoft.com/en-us/azure/architecture/microservices/)

### Frontend

-   Frontend for website and game (user/master)
    
-   Frontend for admin (management)
    

### Backend

-   Backend for Auth/account
    
-   Backend for Game server
    

-   Chat
    

-   Backend for statistics
    
-   Backend Emailer
    
-   Backend Admin
    

  

## Tech (kinda repeat of techstack 🙂)

### Cloud

-   [Azure service bus](https://learn.microsoft.com/en-us/azure/service-bus-messaging/) message broker
    
-   [Database options for azure](https://learn.microsoft.com/en-us/azure/?product=databases)
    
-   [Azure Service Fabric](https://learn.microsoft.com/en-us/azure/service-fabric/service-fabric-overview)
    

#### Scaling (Later on in the course)

-   kubernetes and some azure service to scale [AKS](https://learn.microsoft.com/en-us/azure/architecture/reference-architectures/containers/aks-start-here)
    

### Node

-   [knex](https://knexjs.org/) SQL query builder for database functionality and migrations
    
-   [Prisma](https://www.prisma.io/) ORM tool with migrations
    
-   [Sequelize](https://sequelize.org/) ORM tool with migrations
    
-   typeORM
    

### Python

-   [SQLAlchemy](https://alembic.sqlalchemy.org/en/latest/tutorial.html) ORM / migrations (Alembic)
    

  

### Message queue/broker

-   RabbitMQ
    
-   [Azure service bus](https://learn.microsoft.com/en-us/azure/service-bus-messaging/)
    

### Database

[Database options for azure](https://learn.microsoft.com/en-us/azure/?product=databases)

  

To implement the CQRS pattern we should use both SQL and NoSQL DBs

  

could also just be hosted on a VM with whatever we want?

  

SQL: MySQL, MariaDB, PostgreSQL

  

NoSQL: MongoDB, Elasticsearch, Neo4j

  

## Documentation

openAPI for api documentation

mro for database documentation, maybe some diagrams?

  
  

## CI/CD

Under construction :)

  

It’s possible (if we decide to use Azure for hosting) to have a pipeline from github -> cloud
