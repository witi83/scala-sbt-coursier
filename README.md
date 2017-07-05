# Scala sbt-coursier launcher Dockerfile (alpine)

This Dockerfile integrates [sbt-coursier](http://get-coursier.io), a plugin for [Scala](https://www.scala-lang.org/) and its launcher [csbt](https://github.com/coursier/coursier/blob/master/csbt), an alternative sbt launcher, which avoids sbt's slow bootstrapping and dependency resolution.

Dependencies:
* base image: openjdk:8-alpine 
* sbt-coursier 1.0.0-RC6

## Installation

### github

```
git clone git@github.com:witi83/scala-sbt-coursier.git
cd scala-sbt-coursier
docker build -t witi83/scala-sbt-coursier
docker tag witi83/scala-sbt-coursier scala-sbt-coursier
```

## Usage
Navigate to your scala project, assign the current working directory as mounting point and open the sbt shell:

`docker run -v $PWD:/home/user/app -it --rm scala-sbt-coursier shell`

You may also mount the host's `.coursier` cache directory to improve the startup time even further:

```
time docker run -v $PWD:/home/user/app -v ~/.coursier:/home/user/.coursier -it --rm witi83/scala-sbt-coursier scalaBinaryVersion
[warn] Executing in batch mode.
[warn]   For better performance, hit [ENTER] to switch to interactive mode, or
[warn]   consider launching sbt without any commands, or explicitly passing 'shell'
[info] Loading project definition from /home/user/app/project
[info] Set current project to app (in build file:/home/user/app/)
[info] 2.12

real	0m9,184s
user	0m0,010s
sys	0m0,003s
```

## References
* [scala-sbt](https://github.com/hseeberger/scala-sbt)

## License

This code is open source software licensed under the [Apache 2.0 License]("http://www.apache.org/licenses/LICENSE-2.0.html").