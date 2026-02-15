# my-gradle-convention-plugin

## What is this?

This is a sample [gradle convention plugin](https://docs.gradle.org/current/userguide/implementing_gradle_plugins_convention.html) project, that you could use as a reference.

This project contains [the conventions](/src/main/groovy), that could be applied to the projects that imports this plugin. That way either you can standardize or enforce and achieve common goals in your team or company.

## Usage

In your build.gradle,
```groovy
plugins {
    id 'my-all-standards-convention' version '1.0.0'
}
```
This will bring in all the conventions.

## Task

The conventions are re-grouped under **my-group** so, you can execute them individually. 

These task are wired as part of either build or test. Refer respective [plugin's groovy](/src/main/groovy) for more info.