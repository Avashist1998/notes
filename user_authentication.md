# User Authentication

## Description

User authentication has two part
1. Identify the user
2. Define user privileges.


## Background

There are two ways to perform user authentication
1. Sessions
    Cookie base server sessions.
    Steps
    - First the user logins
    - Store Session is created on the server and sent to the client
    - client saves the session in the cookie
    - request with the session id is make and is checked on the server side

    Drawbacks
    - Cross-site request forgery
    - The team has to store and manage the server session in the database
    - Bottle neck to scaling horizontally

2. User Tokens
    Token are managed by the client and not by the server
    Steps
    - First the user logins
    - Server generates a JWT adn JWT is created with a private key on the server
    - Clients puts JWT in local storage
    - In the future request the JWT is sent in the head to validate
    - Then the server only needs to validate the signature
    
    Drawbacks
    - Token can be high jacked by attackers
    - They are difficult to validate