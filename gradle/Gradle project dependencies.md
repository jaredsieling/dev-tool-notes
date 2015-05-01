## Including local libraries in an app

Typically, when you include dependencies in the build.gradle file of an Android or other app project, you specify a repository of artifacts (often remote repository of jcenter or mavenCentral, etc), and then you use something like

```
compile 'com.squareup.okhttp:okhttp:2.3.0'
```

to specify the coordinates of the artifact you want from that repo. Then when you build, gradle automatically fetches the artifacts and includes.

However, if you want to use a library project you have on your local machine, say during development or something, and not have that code reside in the lib folder in your app, you need to specify the location of the local project directory.

This can be done in two steps:

1. Add the location of the module to the 'settings.gradle' file in the app project.
2. Add the module to the 'build.gradle' dependencies section.

An example with Android, where the library project name is 'SampleLibrary', and the library module within that is 'client_library'.

In the settings.gradle file you would have:

```
include ':app', '..:SampleLibrary:client_library'
```

and in the build.gradle file you would have:

```
compile project(':..:SampleLibrary:client_library')
```
