# node demo app

## Docker
```
docker build -t yourlogin/node-demo-app .
docker push yourlogin/node-demo-app
```

## Debian package (\*.deb file)
```
docker build -t builddep -f Dockerfile.builddep .
docker run -it -v $PWD:/root builddep
cd /root
apt-get install -y npm    # install npm to be able to run npm install
git-buildpackage          # creates *.deb file in node-demo-app_<version>_<arch>.deb
cp ../*.deb .             # *.deb file is created 1 level lower, copy it to current level so it is saved in the volume
exit                      # exit container
```
