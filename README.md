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
- version: (**! version installed on your PC !**) — Latest is **1.2.0**

### Terminal
To generate project workspace with this archetype in your directory use:\
`mvn archetype:generate -DarchetypeArtifactId="JavaArchetype" -DarchetypeGroupId="cz.matesssaks.archetype" -DarchetypeVersion="1.2.0"`\
The new folder, containing workspace, with name of *artifactId* you specified will be created. 

### VS CODE
Installed archetype can be found in VS CODE using extension: **Maven for Java**.

### What next?
After you successfully created your new workspace, go configure [pom.xml][pom], you can add your web page URL, set project description, specify project license, add developer list, [configure project](#configuration), add dependencies and more. :smiley:

## Configuration
For some basic project configuration checkout `<properties>` tag in your workspace's [pom.xml][pom].\
Available properties:
- **project.build.sourceEncoding** (Default: *UTF-8*) — Project encoding
- **mainClass** (Default: *[package].App*) — Project's main class, more at [Code Execution](#code-execution)
- **args** (Default: *one two three*) — Arguments supplied to program when ran, separated with space, more at [Code Execution](#code-execution)
- **maven.compiler.source** (Default: *1.7*) — `-source` argument for java compiler (source compatibility with specified release)
- **maven.compiler.target** (Default: *1.7*) — `-target` argument for java compiler (minimum targeted JVM version that can run compiled classes)
- **maven.compiler.showDeprecation** (Default: *false*) — Show source locations of deprecated APIs
- **maven.compiler.showWarnings** (Default: *false*) — Show compilation warnings

All properties can be quickly overridden on command line with `-D(property)` argument.\
Example: `mvn compile -Dmaven.compiler.showDeprecation=true`

## Code execution
If you want to run your code there are several options:
- **`mvn exec:java`** — Execute main class from compiled classes in `build/classes` directory. Libraries are loaded from local Maven repository on your computer. `mvn compile` is needed to be run before.
- **`mvn exec:exec@jar`** — Execute main class from jar file in `build/` directory. Libraries are loaded from `build\lib` directory. See [Library copying](#library-copying-process). `mvn package` is needed to be run before.
- **`mvn exec:exec@jar-nolib`** — Execute main class from jar file in `build/` directory. No libraries are loaded. `mvn package` is needed to be run before.

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
Contributions are welcome!\
If you want to contribute to this project, make sure you increase the lowest (patch) version number in JavaArchetype's [pom.xml](pom.xml) and in this [README.md](README.md) (Example: 1.0.2 -> 1.0.3).\
If we think other version change is needed, you will be contacted by PR chat.

[pom]: src/archetype-resources/pom.xml