# Getting started with Lerna using plain JS (without Yarn workspaces)

## Basic: Create commons and server npm packages under modules

1. Expose a function from commons called greet
2. Consume the function in server. Specify the dependency in server with the same name and version used in commons package.json
3. Run lerna bootstrap. This will sym link commons to server properly
4. Run the server

## Publishing via lerna
Publish git tags based on lerna version. Note that this increments the version for all submodules(npm versions)
It also seems like it automatically runs bootstrap to updated the sym links
`lerna publish --skip-npm`

## When an individual module is updated
Assume commons was updated (A new commit was added, which optionally increments the version)
```
>lerna updated
lerna info Looking for changed packages since v0.0.2
commons
lerna success found 1 package ready to publish
```

However, without publishing or bootstrapping again, the same symlinks still hold true.
If you run the server, even if the server specifies the older version, 
the updated greet function will come into effect. But in an ideal environment, the dependencies
would be fetched from an internal npm repository. 
Note that for demo purposes here, we skip the npm repo

However, assume that common didn't change it's version. But made other commits with changes
lerna updated will find both modules changed

## Other links
- https://www.toptal.com/front-end/guide-to-monorepos