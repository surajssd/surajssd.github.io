+++
date = "2017-03-14T00:31:57+05:30"
title = "test kompose"

+++

I generally do kompose package testing for fedora. So here are the steps I follow.

Spin the fedora environment, let's say fedora 25.

```
$ docker run -it fedora:25 bash
```

Once inside the container download the latest package from the testing repo:

```
# dnf --enablerepo updates-testing -y install kompose
```

Note: Make sure you download the latest release, there might be conditions that you download the old package.



Now having the package is not enough, we need the functional tests, which is in the source repo. But before we clone the repo, we need some dependencies like `make` and `jq`.

```bash
# dnf install -y jq make
```

Now lets get the functional tests:

```
# git clone https://github.com/kubernetes-incubator/kompose/
# cd kompose
```

Run tests:

```bash
# make test-cmd
```

If all tests pass then just give a karma for it on the release page.

