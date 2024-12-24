# gradle-subprojects-quarkus
Reproducer for Gradle configured subprojects for failing "quarkus update"

#### `cd` to top level(..../gradle-subprojects-quarkus)

1.  execute `gradlew quarkusDev`
2.  browse `localhost:8080` to ensure app works
3.  cancel quarkusDev(ctrl-c or enter `q`)
4.  execute `quarkus update`
5.  should get the following:  

```
Task :library-a:quarkusUpdate
quarkusUpdate is experimental, its options and output might change in future versions
Looking for the newly published extensions in registry.quarkus.io
Detected project Java version: 21
Detected project Java version: 21
Instructions to update this project from '3.17.4' to '3.17.5':
Recommended Quarkus platform BOM updates:
Update: io.quarkus.platform:quarkus-bom:pom:3.17.4 -> 3.17.5

Extensions from io.quarkus.platform:quarkus-bom:

Resolved io.quarkus:quarkus-update-recipes:LATEST with 0 recipe(s) to update from 3.17.4 to 3.17.5 (initially made for OpenRewrite GRADLE plugin version: 6.18.0) 
OpenRewrite recipe generated: /tmp/quarkus-project-recipe-12744013102496327041.yaml



 ------------------------------------------------------------------------
Executing:
/home/daveo/work/quarkus/gradle-subproject/sample_convention_plugins-groovy-dsl/library-a/gradlew --console plain --stacktrace --init-script /tmp/openrewrite-init5842598309085172523gradle rewriteRun

Starting a Gradle Daemon, 1 incompatible Daemon could not be reused, use --status for details

FAILURE: Build failed with an exception.

* Where:
Initialization script '/tmp/openrewrite-init5842598309085172523gradle' line: 23

* What went wrong:
No signature of method: org.gradle.api.internal.artifacts.dsl.dependencies.DefaultDependencyHandler.rewrite() is applicable for argument types: (String) values: [org.openrewrite:rewrite-java]
Possible solutions: wait(), wait(long), create(java.lang.Object), with(groovy.lang.Closure), getAt(java.lang.String)
> Could not find method rewrite() for arguments [org.openrewrite:rewrite-java] on object of type org.gradle.api.internal.artifacts.dsl.dependencies.DefaultDependencyHandler.
```
