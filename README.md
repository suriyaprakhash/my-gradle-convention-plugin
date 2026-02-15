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

## Guardrails

### PMD

The PMD dose not allow to explicitly turn off or configure,
```groovy
pmd {
    ignoreFailures = true
}
```
or
```groovy
pmd {
	maxFailures = 1
}
```

PMD uses the gradle's ruleSet by default, but if you want to configure your own, update the following in pmd-convention groovy file,
```groovy
pmd {
    ruleSetFiles = files("${project.rootDir}/config/pmd/my-custom-rules.xml")
}
```

### JACOCO

To exclude, add the following in the consuming app's **build.gradle**,
```groovy
jacocoExcludes = [
    '**/MySpecificFile.class',          // 1. A specific single file (anywhere)
    'com/pkg/InternalHelper.class',     // 2. A specific file in a specific path
    '**/generated/*.class',             // 3. All classes in a 'generated' folder
    '**/*Dto*',                         // 4. Any class with 'Dto' in the name
    '**/legacy/**'                      // 5. Everything inside the 'legacy' folder
]
```