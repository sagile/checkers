# checkers
Cosmos Developer Portal [Hands-on Exercise tutorial](https://tutorials.cosmos.network/hands-on-exercise/1-ignite-cli/1-ignitecli.html)

## Add Dockerfile-ubuntu
Run:
`docker build -f Dockerfile-ubuntu . -t checkers_i`

Check version:
`docker run --rm -it checkers_i ignite version`

Run container:
```
//?? docker create --name checkers -i -v $(pwd):/checkers -w /checkers -p 1317:1317 -p 3000:3000 -p 4500:4500 -p 5000:5000 -p 26657:26657 checkers_i
//?? docker start checkers
```

`docker run --rm -it -v $(pwd):/checkers -w /checkers checkers_i ignite scaffold chain github.com/sagitoptal/checkers`

## cd checkers
`docker run --rm -it -v $(pwd):/checkers -w /checkers -p 1317:1317 -p 3000:3000 -p 4500:4500 -p 5000:5000 -p 26657:26657 --name checkers checkers_i ignite chain serve`


## Interact via the CLI
From new terminal:
`docker exec -it checkers bash -c "checkersd status 2>&1 | jq"`

## Open UI
`docker exec -it checkers bash -c "cd vue && npm install"`
`docker exec -it checkers bash -c "cd vue && npm run dev -- --host"`

Go to http://localhost:3000

Then connect wallet and send to wallet address via
http://localhost:4500/#/default/post_
Now see assets in ui

## Send message
Stop run, git commit, and do:
`docker run --rm -it -v $(pwd):/checkers -w /checkers checkers_i ignite scaffold message createPost title body`

