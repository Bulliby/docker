# Minimal architecture for Symfony

## Content : 

* PHP8.1
* Apache

## Archlinux default PKGBUILD

[PKGBUILD](https://github.com/archlinux/svntogit-packages/tree/packages/php/trunk)

## Starting a new project :

```shell
docker exec -it belote-docker-auth-1 su www-owner -c 'git config --global user.email "mailhere@gmail.com"'
docker exec -it belote-docker-auth-1 su www-owner -c 'git config --global user.name "Firstname Lastname"'
docker exec -it belote-docker-auth-1 su www-owner -c 'symfony new . --version="6.0.*" --webapp'
```
