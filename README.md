## Test Locally

```
pnpm run bootstrap
pnpm run build
```

Output should look something like this:

```
    > @ build /home/user/pnpm-docker-failure
    > pnpm recursive run build


    packages/package1                        |       build$ echo package1
    packages/package1                        |       build: package1

    packages/package2                        |       build$ echo package2
    packages/package2                        |       build: package2
```

## Test Docker

Start a Docker container with:

```
docker container run \
    --rm \
    --interactive \
    --tty \
    --mount type=bind,source=`pwd`,destination=/code \
    --workdir /code \
    node:10.5.0 \
    bash
```

Then run

```
npm install --global pnpm
pnpm run bootstrap
pnpm run build
```

Output should look like:

```
    > @ build /code
    > pnpm recursive run build


    packages/package1                        |       build$ echo package1

    packages/package2                        |       build$ echo package2
```

