# Docker PHProject

Image to run PHProjects v5 apps in docker

## Quick reference

### Build the image:

```
docker build -t davidetriso/phproject:[tagname-dir_name] ./[tagname-dir_name]
```

E.g.:

```
docker build -t davidetriso/phproject:php-7.4 ./php-7.4
```

### Push image to Docker Hub

```
docker push davidetriso/phproject:tagname
```

E.g.:

```
docker push davidetriso/phproject:php-7.4
```

## How to use

* mount your app code in the `/var/www/html` dir inside the container using bind mounts 
* mount a volume in the `/var/www/html/upload` dir to store persistent files
* create a bind mount in `/etc/apache2/sites-enabled/` to pass your own apache2 conf files to the container

For example, in a compose file add:

```yaml
volumes:
    - ./backend/:/var/www/html
    - uploads:/var/www/html/upload
    - ./conf/sites-enabled/:/etc/apache2/sites-enabled/
```

The image always starts a production server.
