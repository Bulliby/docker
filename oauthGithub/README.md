# oauthGithub

This application permit to request an api token on fully fronted app without **expose** your CLIENT_ID and CLIENT_SECRET by acting like a **proxy**.

This is a php application running on **Apache**.

## Docker image

The image is available on **dockerhub** : [here](https://hub.docker.com/r/waxer/gitgraph)

## Sources

You can find the sources of the **php app** : [here](https://github.com/Bulliby/oauthGithub)

```shell
docker run --name gitgraph --restart=unless-stopped --env CLIENT_SECRET="****" --env  CALLBACK_URL="https://gitgraph.wellsguillaume.fr"  --env CLIENT_ID="****"  --ip 172.17.0.3 -v /home/waxer/dev/oauthGitgraph:/srv/http -d -p 127.0.0.1:23000:80 waxer/gitgraph:v1
```

## Usage

Create a GitHub **OAuth** app in the settings of your **profile**. Put the homepage and callback url of your application. In return get your Client ID and Client secret and use it in `docker run` cmd like above.

Follow this repository to find how a create an **app** who us the docker's environment variables [oauthGitgraph](https://github.com/Bulliby/oauthGitgraph)

## Notes

- Follow this link for configure an **Apache proxy** who serve your different docker **container** : [apache_proxy](https://github.com/Bulliby/development/blob/master/web-server.md).

- Follow this link to configure an ssl connection with **certbot** : [https](https://github.com/Bulliby/development/blob/master/certbot.md)

