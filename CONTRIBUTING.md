# Contributing
Help us improve this project, all contributions are welcome!

Do you have great idea, that will make this project better, or you found some bug or other issue, even a grammar/spelling mistake? If so, you are in the right place to start!

Before creating Pull Request or sending us some Issue, please read these guidelines, it will save time of other developers helping develop and manage this open-source project. Thank you :smile:.

### Please...
- Consider using ours predefined templates.
- Don't create non-project Issues.
- Don't create huge Pull Requests and rather split them to smaller ones focusing on specific update.

## Getting Started
1. Create your own fork of the code.
2. Do the changes in your fork.
3. If you think you are done with editing, continue in [Pull Requests Process](#pull-requests-process).

## Code Style
- For indentation use tabulators.
- If you are writing one line comment, use Start (`<!--`) and End (`-->`) at the same line and make sure you place one space after Start and one space before End. Example:
  ```
  <!-- SOME HEADING -->
  <!-- <some>code</some> -->
  ```
- If you are writing two or more lined comment, use Start (`<!--`) and End (`-->`) at its own separated lines. Example:
  ```
  <!--
  <commented>
    <code>foo</code>
  </commented>
  -->
  ```

## Pull Requests Process
1. If you invent something new to project, update [README.md](README.md) with description of new features.
2. If your changes are a patch, update patch (lowest) version number in [pom.xml](pom.xml) (Example: 1.0.1 -> 1.0.2), otherwise update minor version number (Example: 1.1.1 -> 1.2.0).\
(If we think other version change is needed, you will be contacted by PR chat.)
3. Update all occurrences of project version in [README.md](README.md).
4. Make sure you have followed the [Code Style](#code-style) for the project.
5. Create Pull Request, fill out its template and write simple message to it. (Please notice [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md))

## Code of Conduct
See [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md)