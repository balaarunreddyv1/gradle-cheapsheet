- Gradle Project is a collection of tasks.
- task is a collection of actions.
- Actions are functions performed by gradle in a acylic way.

**NOTE:** Gradle properties are based on gradle closure. so a block of code in a gradle closure `{ code }` is executed runtime.

- Gradle uses Project Object Model. so every sytnax in the build.gradle file extends `project` object. **example:** `repositories { mavencentral() }` can also declared as `project.repositories { mavencentral() }`

**Proerties in a gradle file**
- To list all the properties what can used in build.gradle file -> run terminal command `gradle properties`. or search in https://docs.gradle.org/current/dsl/org.gradle.api.Project.html

**Tasks** https://docs.gradle.org/current/dsl/org.gradle.api.Task.html#org.gradle.api.Task
- To view all available gradle tasks run `gradle tasks` command. 
- tasks depend on other tasks `example: tasks.B.dependsOn 'A'`. -> task A gets excuted first and them task B get executed.
```Example: 
task B {
    dependsOn A  // Task A gets executed first
    group = 'my task' // assigns the task to a task group.
    descripton = "task descripton"
}
```
- Can Extend a exsisting task  

**List all projects in repo**
- `./gradlew projects`

**Dependencies**
- find dependecines and its dependencies `./gradlew dependencies` or `./gradlew dependencies --configuration compile` <- runs only the 

- `settings.gradle` has the project structure and its child projects included for project scope purpose. 
```
example: settings.gradle

rootProject.name=Parent-project
include 'child-project'

```
- buildScript { dependencies { } }  // used to point files. classes that required at buildtime.

- Gradle project can have multiple child gradle projects. To find the gradle child projects look at setting.gradle file. with syntax `include ${new-project}` where `new-project` is a child gradlw project. this child project has it own build.gradle file.

- A gradle child project can used as a dependency in other gradle project.
````
Example: project-a has dependency on project-b

In project-a build.gradle

dependencies {
    compile project(':project-b') <- declared project-b as requiered at compile for project-a, and project-a build artifact will include project B aswell.
}
````

- build directory is the output directory of gradle.

- use `-q` to run commands in quite mode. example: gradle -q projects

**gradle wrapper**
- gradle wrapper aka gradlew makes sure that proper gradlew version is installed properly.
gradlew wrapper reads the settings from `gradle-wrapper.properties` located under `projectDir/gradle/wrapper/`

**gradle --profile**
- generates a report for the ran task profile `example: gradle build --profile` generate a build profile summary report.
