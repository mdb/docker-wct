# docker-wct

A Docker image for running [web-component-tester](https://github.com/Polymer/web-component-tester) tests against [Google Polymer](https://github.com/Polymer/polymer) elements and applications in Firefox and Chrome with no GUI.

## Building from the `Dockerfile`

Building requires that you've installed and are running Docker.

```
git clone https://github.com/mdb/docker-wct.git
cd docker-wct
docker build -t your-image-name .
```

## Example usage

```
git clone https://github.com/PolymerElements/iron-ajax.git

docker run -it \
  -v $(pwd)/iron-ajax:/usr/src/app \
  --security-opt seccomp:unconfined \
  mdb/wct bash \
  -c "/usr/bin/bower install && /usr/bin/xvfb-run wct --skip-selenium-install"
```
