# oauthGithub8

This application permit to request an api token on fully fronted app without **expose** your CLIENT_ID and CLIENT_SECRET by acting like a **proxy**.

This is a php application running on apache.

## Sources

You can find the sources here : [oauth](https://github.com/Bulliby/oauthGithub)

## Docker

You can use the docker hub image here : [dockerhub](https://hub.docker.com/r/waxer/oauth_github)

```shell
docker run --name gitgraph --restart=unless-stopped --env CLIENT_SECRET="*******" --env  CALLBACK_URL="http://client.gitgraph.com"  --env CLIENT_ID="*****"  -v /home/waxer/dev/PHP/oauthGitgraph:/srv/http -d -p 23000:80 oauth_github
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

