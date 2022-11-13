# Minimal architecture for Symfony

## Content : 

* PHP 8.1
* Apache

## Starting a new project :

```shell
docker exec --user www-owner -it container-name 'touch toto'
docker build --build-arg MAIL="gustavo@gmail.com" --build-arg SIGNATURE="Gustavo Dupond" -t waxer/symfony .
```
