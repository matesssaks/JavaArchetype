# JavaArchetype
Simple Maven archetype for Java development.

JavaArchetype is predefined workspace structure, containing preconfigured [pom.xml][pom], [.gitignore](src/archetype-resources/.gitignore) and example project [App.java](src/archetype-resources/src/App.java) with example test [AppTest.java](src/archetype-resources/tests/AppTest.java).

## JavaArchetype project structure:
<pre>
project
├── <a href="src/archetype-resources/pom.xml">pom.xml</a>
├── <a href="src/archetype-resources/.gitignore">.gitignore</a>
├── src (<b>Project sources and resources</b>)
│   └── (project package)
|       └── <a href="src/archetype-resources/src/App.java">App.java</a> (Example project)
├── tests (<b>Project tests</b>)
│   └── <a href="src/archetype-resources/tests/AppTest.java">AppTest.java</a> (Example test)
└── build (! created after compile !)
    ├── classes (Compiled project)
    |   └─ (project package)
    |      └─ App.class (Example project, compiled)
    ├── tests (Compiled tests)
    |   └─ AppTest.class (Example test, compiled)
    └─ project.jar (Example project, packaged)
</pre>

## Installation
1. Download the latest source code with git (`git clone https://github.com/matesssaks/JavaArchetype`) or as [zip](https://github.com/matesssaks/JavaArchetype/archive/main.zip).
2. Go to the folder with main [pom.xml](pom.xml). Example: `cd JavaArchetype`.
3. Install to your local Maven repository with `mvn install`.

## Creating workspace with JavaArchetype
For proper usage you need to know:
- group ID: **cz.matesssaks.archetype**
- artifact ID: **JavaArchetype**
- version: (**! version installed on your PC !**) — Latest is **1.3.0**

### Terminal
To generate project workspace with this archetype in your directory use:\
`mvn archetype:generate -DarchetypeArtifactId="JavaArchetype" -DarchetypeGroupId="cz.matesssaks.archetype" -DarchetypeVersion="1.3.0"`\
The new folder, containing workspace, with name of *artifactId* you specified will be created. 

### VS CODE
Installed archetype can be found in VS CODE using extension: **Maven for Java**.

### What next?
After you successfully created your new workspace, go configure [pom.xml][pom], you can add your web page URL, set project description, specify project license, add developer list, [configure project](#configuration), add dependencies and more. :smiley:

## Configuration
For some basic project configuration checkout `<properties>` tag in your workspace's [pom.xml][pom].\
Available properties:
- **project.build.sourceEncoding** (Default: *UTF-8*) — Project encoding
- **mainClass** (Default: *[package].App*) — Project's main class. See [Code Execution](#code-execution).
- **args** (Default: *one two three*) — Arguments supplied to program when ran, separated with space. See [Code Execution](#code-execution).
- **exec.java** (Default: *java*) — Path/command to java binary, used by `exec:exec`, see [Code Execution](#code-execution).
- **skipTests** (Default: *false*) — Skip tests. Tests will still compile, but will not be runned.
- **maven.compiler.source** (Default: *7*, **disabled**) — `-source` argument for java compiler (source compatibility with specified release, **use with JDK 8 and lower**)
- **maven.compiler.target** (Default: *7*, **disabled**) — `-target` argument for java compiler (minimum targeted JVM version that can run compiled classes, **use with JDK 8 and lower**)
- **maven.compiler.release** (Default: *7*) — `-release` argument for java compiler (replaces `-source`, `-target` and `-bootclasspath` arguments, better version cross-compilation, **! available only in JDK 9 and beyond !**)
- **maven.compiler.showDeprecation** (Default: *false*) — Show source locations of deprecated APIs
- **maven.compiler.showWarnings** (Default: *false*) — Show compilation warnings
- **maven.jar.addMavenDescriptor** (Default: *true*) — Include project's [pom.xml](pom) and *pom.properties* file in exported JAR.
- **maven.jar.addClasspath** (Default: *true*) — Add required runtime dependencies to JAR Manifest's Classpath.
- **maven.jar.classpathPrefix** (Default: *lib*) — Path to directory containing required runtime dependencies, relative to JAR location. Leave empty if dependencies are in same folder as JAR.
- **maven.jar.mainClass** (Default: *${mainClass}*) — Location of main class in JAR, needed when creating executable JAR. Leave empty if you don't want JAR executable (e.g. library).
- **maven.jar.addDefaultImplementationEntries** (Default: *false*) — Add these entries to JAR Manifest:
<pre>
<b>Implementation-Title</b>: ${project.name}
<b>Implementation-Version</b>: ${project.version}
<b>Implementation-Vendor</b>: ${project.organization.name}
</pre>
- **maven.jar.addDefaultSpecificationEntries** (Default: *false*) — Add these entries to JAR Manifest:
<pre>
<b>Specification-Title</b>: ${project.name}
<b>Specification-Version</b>: ${project.artifact.selectedVersion.majorVersion}.${project.artifact.selectedVersion.minorVersion}
<b>Specification-Vendor</b>: ${project.organization.name}
</pre>
- **maven.jar.addBuildEnvironmentEntries** (Default: *false*) — Add these entries to JAR Manifest:
<pre>
<b>Build-Tool</b>: ${maven.build.version}
<b>Build-Jdk</b>: ${java.version} (${java.vendor})
<b>Build-Os</b>:  ${os.name} (${os.version}; (${os.arch})
</pre>

All properties can be quickly overridden on command line with `-D(property)` argument.\
Example: `mvn compile -Dmaven.compiler.showDeprecation=true`

## Code execution
If you want to run your code there are several options:
- **`mvn exec:java`** — Execute main class from compiled classes in `build/classes` directory. Libraries are loaded from local Maven repository on your computer. `mvn compile` is needed to be run before. To attach debugger to program, use `mvnDebug`, example: `mvnDebug exec:java`.
- **`mvn exec:exec@jar`** — Execute main class from jar file in `build/` directory. Libraries are loaded from `build\lib` directory. See [Library copying process](#library-copying-process). `mvn package` is needed to be run before. Doesn't work with `mvnDebug`.
- **`mvn exec:exec@jar-nolib`** — Execute main class from jar file in `build/` directory. No libraries are loaded. `mvn package` is needed to be run before. Doesn't work with `mvnDebug`.

To make Maven less annoying run `mvn` or `mvnDebug` with `-q` (quiet) parameter. Example: `mvn -q exec:java`

If you want run `mvnDebug` on different port (default is 8000), you must locate and edit `mvnDebug` script on your PC or obtain new at [Maven's GitHub](https://github.com/apache/maven/tree/master/apache-maven/src/assembly/maven/bin).

## Library copying process
All libraries needed by program in runtime are copied to `build/lib` folder. This copying process is bound to Maven's *package* phase (See [Maven Build Lifecycle](https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html)).

## License
```
Copyright 2020 matesssaks

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```

## Contributing
Help us improve this project, see [CONTRIBUTING.md](CONTRIBUTING.md) for more info.