# Ghost-Theme-Dev-Env
This is an environment for doing Ghost Theme Development in a docker container

## The Setup
The idea here is just clone this repository to get the files, it should not really remain a git repo.

```
git clone --depth=1 --branch=master --recurse-submodules git@github.com:CryDeTaan/Ghost-Theme-Dev-Env.git
```
Change direcotry to cloned repo
```
cd Ghost-Theme-Dev-Env/
rm -rf .git
```

## Run docker

```
docker run -d \
  --name blog \
  -e url=http://localhost:3001 \
  -p 3001:2368 \
  -v $(pwd)/data/:/var/lib/ghost/content/data/ \
  -v $(pwd)/themes/:/var/lib/ghost/content/themes/ \
  ghost
```
- `--name blog` Name of container
- `-e url=http://localhost:3001` URL to Dev env
- `-p 3001:2368` Exposed port
- `-v $(pwd)/data/:/var/lib/ghost/content/data/` Database - So that it is not needed to the go through the regestration process each time.
- `-v $(pwd)/themes/:/var/lib/ghost/content/themes/` blog - The name of the theme
- `ghost` Docker image to run

With that you'll be able to navigate to http://localhost:3001 or http://localhost:3001/ghost
**Username** | **Password**
------------ | -------------
theme.developer@ghost.local | Notsecure123

## Theme location

At this point you can add any themes to the themes directory
```
cd themes
mkdir <new theme>
cd <new theme>
```
Once you are in the new theme directory, you can start you theme development, this is also where you want to `git init` to make use of the theme in your ghost production site.

For more information regarding ghost theme development, please see: https://ghost.org/docs/api/v3/handlebars-themes/
