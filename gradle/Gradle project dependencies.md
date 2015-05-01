## Including local libraries in an app

Typically, when you include dependencies in the build.gradle file of an Android or other app project, you specify a repository of artifacts (often remote repository of jcenter or mavenCentral, etc), and then you use something like

```
compile 'com.squareup.okhttp:okhttp:2.3.0'
```

to specify the coordinates of the artifact you want from that repo. Then when you build, gradle automatically fetches the artifacts and includes.

However, if you want to use a library project you have on your local machine, say during development or something, and not have that library (.jar or .aar file) reside in the libs folder in your app, you need to specify the location of the local project directory.

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

NOTES:

1. This assumes the library project directory is at the location ../ relative to the app project directory.
2. If you are doing this just for development, be sure to change the library location in the dependencies back to remote repo, if you don't want others who are using the library to have to install it locally on their machines.  You would of course need to publish the library (jcenter or mavenCentral) before they could use it.
3. Another option, instead of point to the local library module and having it build when you build the app, is to publish the artifact to your local repository, with something like 'gradle uploadArchives'.  
