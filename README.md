# NetObserv patch content

This package is patched to allow JSON (de)serialization.

Assuming you have "upstream" set as the prometheus upstream remote, and "netobserv" set as the netobserv patched remote, e.g:

```bash
$ git remote -v
netobserv	git@github.com:netobserv/prometheus-common.git (fetch)
netobserv	git@github.com:netobserv/prometheus-common.git (push)
upstream	https://github.com/prometheus/common.git (fetch)
upstream	https://github.com/prometheus/common.git (push)
```

Steps to rebase:

```bash
tag=v0.55.0 # the tag to rebase on
git fetch upstream ; git fetch netobserv
git reset --hard $tag
git cherry-pick netobserv/main
git tag -a "$tag-netobserv" -m "$tag-netobserv"
git push netobserv HEAD:main
git push netobserv --tags
```


# Common
![circleci](https://circleci.com/gh/prometheus/common/tree/main.svg?style=shield)

This repository contains Go libraries that are shared across Prometheus
components and libraries. They are considered internal to Prometheus, without
any stability guarantees for external usage.

* **assets**: Embedding of static assets with gzip support
* **config**: Common configuration structures
* **expfmt**: Decoding and encoding for the exposition format
* **model**: Shared data structures
* **promlog**: A logging wrapper around [go-kit/log](https://github.com/go-kit/kit/tree/master/log)
* **route**: A routing wrapper around [httprouter](https://github.com/julienschmidt/httprouter) using `context.Context`
* **server**: Common servers
* **version**: Version information and metrics
