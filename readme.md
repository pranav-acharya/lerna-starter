# Getting started with Lerna using plain JS (without Yarn workspaces)

## Basic: Create commons and server npm packages under modules

1. Expose a function from commons called greet
2. Consume the function in server. Specify the dependency in server with the same name and version used in commons package.json
3. Run lerna bootstrap. This will sym link commons to server properly
4. Run the server