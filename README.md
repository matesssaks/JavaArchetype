# JavaArchetype
Simple Maven archetype for Java development.

## JavaArchetype project structure:
<pre>
project
├── pom.xml
├── .gitignore
├── src (<b>Project sources and resources</b>)
│   └── (project package)
|       └──App.java (Example project)
├── tests (<b>Project tests</b>)
│   └── AppTest.java (Example test)
└── build
    ├── classes (Compiled project)
    |   └─ (project package)
    |      └─ App.class (Example project, compiled)
    └── tests (Compiled tests)
        └─ AppTest.class (Example test, compiled)
</pre>

## Installation
1. Download the latest source code with git (`git clone https://github.com/matesssaks/JavaArchetype`) or as [zip](https://github.com/matesssaks/JavaArchetype/archive/main.zip).
2. Go to the folder with main *pom.xml*. Example: `cd JavaArchetype`.
3. Install to your computer with `mvn install`.

## Usage
For proper usage you need to know:
1. group ID: **cz.matesssaks.archetype**
2. artifact ID: **JavaArchetype**
3. version: (**! version installed on your pc !**) - Latest is **1.1.0**

### Terminal
To generate project workspace with this archetype in your directory use:\
`mvn archetype:generate -DarchetypeArtifactId="JavaArchetype" -DarchetypeGroupId="cz.matesssaks.archetype" -DarchetypeVersion="1.1.0"`

### VS CODE
Installed archetype can be found in VS CODE using extension: **Maven for Java**.

## Contributing
Contributions are welcome!\
If you want to contribute to this project, make sure you increase the lowest (patch) version number in *pom.xml* and in this README.md (Example: 1.0.2 -> 1.0.3).\
If we think other version change is needed, you will be contacted by PR chat.