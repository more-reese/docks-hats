---

# Hats <> DAOhaus Integration Demo App

## Overview

This app is a demonstration of how a moloch dao built on the DAOhaus v3 protocol can manage a Hats tree through DAO proposals.

## What does it do?

View DAO owned Top Hats and sub hats.

[](https://s3.amazonaws.com/charm.public/user-content/6cc7e5c5-24f9-4b10-b406-91992344a4e7/3f81f824-337e-43fc-ac04-8c81a7851d6c/Screenshot-from-2023-04-11-09-34-32.png)

DAO members can make a proposal to:

- Create new top hats

- Create new sub hats

- Mint hats to wearers

[](https://s3.amazonaws.com/charm.public/user-content/6cc7e5c5-24f9-4b10-b406-91992344a4e7/9761e7a6-4917-4714-b0c6-d2da2f19facf/Screenshot-from-2023-04-11-09-29-40.png)

If DAO proposal pass the hats are created upon proposal execution

[](https://s3.amazonaws.com/charm.public/user-content/6cc7e5c5-24f9-4b10-b406-91992344a4e7/7687a8eb-1333-4370-8bd4-e7c54f5fc681/Screenshot-from-2023-04-11-09-34-20.png)
### Next steps

- Create a proposal form for revoking hats

## Implementation Details

Utilizes the DAOHaus v3 protocol tooling for rapid dao-application development:

- Starter repo

- NPM packages

- Moloch v3 contracts and subgraphs

Queries the Hats subgraph to display hat trees owned by this DAO.

Build proposal execution data to make function calls on Hats contracts.

## Links

App\
[https://hats-demo.daohaus.club/](https://hats-demo.daohaus.club/)

Goerli DAO [https://admin.daohaus.club/#/molochv3/0x5/0x052cf3746e2dff16af70bc2184a934dc48d181f7](https://admin.daohaus.club/#/molochv3/0x5/0x052cf3746e2dff16af70bc2184a934dc48d181f7)

Repos: 

[https://github.com/HausDAO/hats-demo](https://github.com/HausDAO/hats-demo) 

[https://github.com/HausDAO/dao-app-starter-vite](https://github.com/HausDAO/dao-app-starter-vite) 

[https://github.com/HausDAO/monorepo](https://github.com/HausDAO/monorepo)