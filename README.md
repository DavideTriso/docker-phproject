# Docker PHProject

Image to run PHProjects v5 apps in docker

## Quick reference

### Build the image:

```
docker build -t davidetriso/phproject:[tagname-dir_name] ./[tagname-dir_name]
```

E.g.:

```
docker build -t davidetriso/phproject:php-7.4-apache ./php-7.4-apache
```

### Push image to Docker Hub

```
docker push davidetriso/phproject:tagname
```

E.g.:

```
docker push davidetriso/phproject:php-7.4-apache
```

## How to use

* mount your app code in the `/var/www/html` dir inside the container using bind mounts 
* mount a volume in the `/var/www/html/upload` dir to store persistent files
* for apache image: create a bind mount in `/etc/apache2/sites-enabled/` to pass your own apache2 conf files to the container
* for fpm images: expose port 9000

Apache example:

```yaml
volumes:
    - ./backend/:/var/www/html
    - uploads:/var/www/html/upload
    - ./conf/sites-enabled/:/etc/apache2/sites-enabled/
```

The image always starts a production server.

