- Gradle Project is a collection of tasks.
- task is a collection of actions.
- Actions are functions performed by gradle in a acylic way.

- Gradle uses Project Object Model. so every sytnax in the build.gradle file extends `project` object. **example:** `repositories { mavencentral() }` can also declared as `project.repositories { mavencentral() }`

To list all the properties what can used in build.gradle -> run terminal command `gradle properties`.
