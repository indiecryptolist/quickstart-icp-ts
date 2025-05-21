# Internet Computer REST Boilerplate

This boilerplate uses Azle to write Internet Computer DApps (ICP Decentralized Apps) using traditional HTTP REST patterns. Use it for backend code. You can use any frontend.

![IndieCrypto Github](https://github.com/user-attachments/assets/6b52aa6b-b572-4269-a552-a79a2634e6c5)

Curated by IndieCrypto <> ICP United Kingdom


## Full Instructions

### Node.js 22

It's recommended to use nvm to install Node.js 22:

```sh
$ curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
```

Restart your terminal and then run:

```sh
$ nvm install 22
```

Check that the installation went smoothly by looking for clean output from the following command:

```sh
$ node --version
```

### dfx

Install the dfx command line tools for managing ICP applications:

```sh
$ DFX_VERSION=0.24.3 sh -ci "$(curl -fsSL https://internetcomputer.org/install.sh)"
```

Check that the installation went smoothly by looking for clean output from the following command:

```sh
$ dfx --version
```

### Deployment

To create and deploy a simple sample application called hello_world:

```
# create a new default project called hello_world
$ npx azle new hello_world --http-server --experimental
$ cd hello_world

# install all npm dependencies including azle
$ npm install

# start up a local ICP replica
$ dfx start --clean
```

In a separate terminal in the hello_world directory:

```sh
# deploy your canister
$ dfx deploy
```

If you would like your canister to autoreload on file changes:

```sh
AZLE_AUTORELOAD=true dfx deploy
```

View your frontend in a web browser at `http://[canisterId].raw.localhost:4943`

To obtain your application's [canisterId]:

```sh
$ dfx canister id backend
```

Communicate with your canister using any HTTP client library, for example using curl:

```sh
curl http://[canisterId].raw.localhost:8000/db
curl -X POST -H "Content-Type: application/json" -d "{ \"hello\": \"world\" }" http://[canisterId].raw.localhost:8000/db/update
```
