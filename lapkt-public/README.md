# LAPKT

[![](https://images.microbadger.com/badges/image/lapkt/lapkt-public.svg)](https://microbadger.com/images/lapkt/lapkt-public "")

This directory contains the Docker definition for an image 
with a number of LAPKT-Based planners


## Available Tools

As of now, the image features the following planners:

* The [LAPKT](http://lapkt.org/) planning toolkit.

Additionally, The image pre-compiles the following planners, which are ready to run:
* bfs_f
* dfs_plus
* siw
* siw_plus
* siw-then-bfsf
* ff

Each of the previous tools lies on the subdirectory `/root/projects/lapkt/compiled_planners`.


## Basic Usage
In order to use the docker images, you need to [have Docker installed on your machine](https://docs.docker.com/engine/installation).
Once that is done, you can pull the image with

```shell
docker pull lapkt/public
```

Then start the container interactively:

```shell
docker run -it lapkt/public
```

and use any of the provided tools, e.g.

```shell
./siw --domain ../benchmarks/ipc-2011/visitall/domain.pddl --problem ../benchmarks/ipc-2011/visitall/problem12.pddl
```

## Advanced Usage

We can run the compiled planners from the host machine:

```shell
docker run -it nirlipo/lapkt \
./siw --domain ../benchmarks/ipc-2011/visitall/domain.pddl --problem ../benchmarks/ipc-2011/visitall/problem12.pddl > output.txt
```

Alternatively, we can use the same technique in order to have some planner output its results to a directory from the host machine:

```shell
docker run -it nirlipo/lapkt \
./siw --domain ../benchmarks/ipc-2011/visitall/domain.pddl --problem ../benchmarks/ipc-2011/visitall/problem12.pddl > output.txt
```

Assume we have, say, some benchmarks on a `~/benchmarks` directory on the host machine, and we want to run some planner in the starter kit on those benchmarks.
We can start the docker container [mounting the desired directory](https://docs.docker.com/engine/tutorials/dockervolumes/#mount-a-host-directory-as-a-data-volume) as follows:

```shell
docker run -it -v ~/benchmarks:/root/projects/benchmarks nirlipo/lapkt
```

and the desired benchmarks will be accessible under `/root/projects/benchmarks`.



## Extending the image
_Work in Progress_

