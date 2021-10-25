# Public reproduction of the issue faced in https://github.com/sbt/sbt/issues/6183

To reproduce
 - Start an sbt shell in this project.
 - Compile the project (`compile`).
 - Change `src/main/scala/A.scala`, for example add `foo bar` at the end of line 3.
 - Compile again (`compile`).

The result should look as follows.

```
> sbt
[info] welcome to sbt 1.5.5 (AdoptOpenJDK Java 11.0.3)
[info] loading global plugins from /Users/jds/.sbt/1.0/plugins
[info] loading project definition from /Users/jds/compile_loop/project
[info] loading settings for project compile_loop from build.sbt ...
[info] set current project to compile_loop (in build file:/Users/jds/compile_loop/)
[info] sbt server started at local:///Users/jds/.sbt/1.0/server/b6c604f4d74dca0fc3da/sock
[info] started sbt server
sbt:compile_loop> compile
[info] compiling 3 Scala sources and 5 Java sources to /Users/jds/compile_loop/target/scala-2.13/classes ...
[success] Total time: 3 s, completed 25 Oct 2021, 20:26:55
sbt:compile_loop> compile
[info] compiling 1 Scala source to /Users/jds/compile_loop/target/scala-2.13/classes ...
[info] compiling 1 Scala source and 1 Java source to /Users/jds/compile_loop/target/scala-2.13/classes ...
[info] compiling 1 Scala source and 1 Java source to /Users/jds/compile_loop/target/scala-2.13/classes ...
[info] compiling 3 Scala sources and 1 Java source to /Users/jds/compile_loop/target/scala-2.13/classes ...
[info] compiling 2 Scala sources and 1 Java source to /Users/jds/compile_loop/target/scala-2.13/classes ...
[info] compiling 3 Scala sources and 1 Java source to /Users/jds/compile_loop/target/scala-2.13/classes ...
[info] compiling 3 Scala sources and 1 Java source to /Users/jds/compile_loop/target/scala-2.13/classes ...
[info] compiling 3 Scala sources and 1 Java source to /Users/jds/compile_loop/target/scala-2.13/classes ...
[info] compiling 3 Scala sources and 1 Java source to /Users/jds/compile_loop/target/scala-2.13/classes ...
[info] compiling 3 Scala sources and 1 Java source to /Users/jds/compile_loop/target/scala-2.13/classes ...
[info] compiling 3 Scala sources and 1 Java source to /Users/jds/compile_loop/target/scala-2.13/classes ...
[info] compiling 3 Scala sources and 1 Java source to /Users/jds/compile_loop/target/scala-2.13/classes ...
[info] compiling 3 Scala sources and 1 Java source to /Users/jds/compile_loop/target/scala-2.13/classes ...
[info] compiling 3 Scala sources and 1 Java source to /Users/jds/compile_loop/target/scala-2.13/classes ...
[info] compiling 3 Scala sources and 1 Java source to /Users/jds/compile_loop/target/scala-2.13/classes ...
[info] compiling 3 Scala sources and 1 Java source to /Users/jds/compile_loop/target/scala-2.13/classes ...
[info] compiling 3 Scala sources and 1 Java source to /Users/jds/compile_loop/target/scala-2.13/classes ...
^C
[warn] Canceling execution...
[error] /Users/jds/compile_loop/src/main/java/reproduction/ABase.java:1:1: cannot access reproduction
[error]   null
Cancelled: compile
[error] Cancelled: compile
[error] Use 'last' for the full log.
sbt:compile_loop>
```
