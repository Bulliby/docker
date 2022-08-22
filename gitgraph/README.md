# Gitgraph docker

```bash
docker run --name gitgraph --restart=unless-stopped --env CLIENT_SECRET="***" --env  CALLBACK_URL="https://url-front.site.fr"  --env CLIENT_ID="***"  --ip 172.17.0.3 -v /path/:/srv/http -d -p 127.0.0.1:23000:80 waxer/gitgraph:8.1
```
