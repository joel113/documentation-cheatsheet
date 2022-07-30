# SBT cheat sheet

## Managing dependencies

Add a dependency:

```
libraryDependencies += "org.apache.derby" % "derby" % "10.4.1.3"
```

Add multiple dependencies:

```
libraryDependencies ++= Seq(
  groupID % artifactID % revision,
  groupID % otherID % otherRevision
)
```

Getting the right scala version:

```
libraryDependencies += "org.scala-tools" % "scala-stm_2.11" % "0.3"
libraryDependencies += "org.scala-tools" %% "scala-stm" % "0.3"
```
https://www.scala-sbt.org/1.x/docs/Library-Dependencies.html
