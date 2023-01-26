# swish

### Build times improvements:
As for this example i was trying to focus on building ci pipeline of this project, my app is very simple and the build time is quick, but there are a lot of ways we can optimize build times of the applications by utilizing some of the techniques such as:
1. Docker layer caching.
2. External cache sources (using --cache-from command arg. There are some prerequisites to making it work. BuildKit backend is required — this requires Docker version ≥18.09 and setting a DOCKER_BUILDKIT=1 environment variable before invoking docker build. The source image should also be built with --build-arg BUILDKIT_INLINE_CACHE=1 so that it has cache metadata embedded.).
3. Multi-stage builds and virtual environments. Basically we can split the dockerfile int stages and build all the app dependencies and in the second stage build the app using only necessary ones.
4. Also we can use .dockerignore where we can specify all kinds of files. Here is an (example)[https://github.com/themattrix/python-pypi-template/blob/master/.dockerignore] of files that could be listed.
I could find more, but think these are the methods that are most common, and that i would try to use first.

###
