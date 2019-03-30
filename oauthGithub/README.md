i# oauthGithub

This application permit to request an api token on fully fronted app without **expose** your CLIENT_ID and CLIENT_SECRET by acting like a **proxy**.

This is a php application running on apache.

## Sources

You can find the sources here : [oauth](https://github.com/Bulliby/oauthGithub)

## Docker

You can use the docker hub image here : [dockerhub](https://hub.docker.com/r/waxer/oauth_github)

```shell
docker run --name oauth_github --env DEV_CLIENT_SECRET="client secret" --env  DEV_GIT_GRAPH_URL="http://gitgraph" --env DEV_CLIENT_ID="client id"  -d -p 23000:80 waxer/oauth_github:v1
```

There is six **environment variable** available :

```shell
DEV_CLIENT_SECRET
DEV_GIT_GRAPH_URL
DEV_CLIENT_ID
PROD_CLIENT_SECRET
PROD_GIT_GRAPH_URL
PROD_CLIENT_ID
```

## Usage

Create a GitHub **OAuth** app in the settings of your **profile**. Put the homepage and callback url of your application. In return get your Client ID and Client secret and use it in `docker run` cmd like above.

- Follow this link for configure an **Apache proxy** who serve your different docker **container** : [apache_proxy](https://github.com/Bulliby/development/blob/master/web-server.md).

- Follow this link to configure an ssl connection with **certbot** : [https](https://github.com/Bulliby/development/blob/master/certbot.md)

