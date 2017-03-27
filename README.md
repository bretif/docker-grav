Deploy [GRAV CMS](https://getgrav.org) on docker

# Quick start
Deploy GRAV
```
docker run -d --name grav -d -p 8000:80 sudokeys/grav
```

Then you can access GRAV on http://127.0.0.1:8000

Deploy GRAV with [admin plugin](https://github.com/getgrav/grav-plugin-admin)
```
docker run -d --name grav -d -p 8000:80 sudokeys/grav-withadmin
```


# Details
This is a basic installation of grav directly from github.
If you want to add more plugins, you can create your own Docker file.

For instance below Dockerfile to install [git-sync](https://github.com/trilbymedia/grav-plugin-git-sync) plugin and [clean-blog](https://github.com/tranduyhung/grav-theme-clean-blog) theme
```
FROM sudokeys/grav

WORKDIR /var/www/html

RUN bin/gpm --no-interaction install git-sync  && \
    bin/gpm --no-interaction install clean-blog
    chown -R www-data:www-data /var/www/html/
```

# Apache / nginx / FPM
Default docker used apache by default.
If needed you can user nginx-fpm image for a more complex but powerfull deployement
