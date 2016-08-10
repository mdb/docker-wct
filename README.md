[![Build Status](https://travis-ci.org/mdb/docker-wct.svg?branch=master)](https://travis-ci.org/mdb/docker-wct)

# docker-wct

A Docker image for running [web-component-tester](https://github.com/Polymer/web-component-tester) tests against [Google Polymer](https://github.com/Polymer/polymer) elements and applications in Firefox and Chrome with no GUI.

## Pull

```
docker pull clapclapexcitement/wct
```

## Example usage

```
git clone https://github.com/PolymerElements/iron-ajax.git

docker run -it \
  -v $(pwd)/iron-ajax:/usr/src/app \
  --security-opt seccomp:unconfined \
  clapclapexcitement/mdb bash \
  -c "/usr/bin/bower install && /usr/bin/xvfb-run wct --skip-selenium-install"
```

Can you give me that as a one liner?

```
docker run -it -v $(pwd)/iron-ajax:/usr/src/app --security-opt seccomp:unconfined clapclapexcitement/wct bash -c "/usr/bin/bower install && /usr/bin/xvfb-run wct --skip-selenium-install"
```

## Building from the `Dockerfile`

Building requires that you've installed and are running Docker.

```
git clone https://github.com/mdb/docker-wct.git
cd docker-wct
docker build -t your-image-name .
```

## Notes on `seccomp`

`seccomp-bpf` extends `seccomp` and allows the filtering of system calls using a configurable policy. It is used by Google Chrome/Chromium web browsers on Chrome OS and Linux.

This requires the use of a suitable profile or `seccomp:unconfined`.

More can be read [here](https://github.com/jlund/docker-chrome-pulseaudio/issues/8).
