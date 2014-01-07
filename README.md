# Gradle WAR overlay plugin

A plugin for gradle to provide functionality similar to the war overlay function in maven. This plugin is initially
developed to support building CAS servers, but should work in other situations. This plugin enhances the [Gradle WAR plugin](http://www.gradle.org/docs/current/userguide/war_plugin.html).

## Configuration

Import the plugin:

```groovy
apply from: "http://dl.bintray.com/scalding/generic/waroverlay.gradle"
```

Add the WAR dependency you want to overlay as a runtime dependency:

```groovy
dependencies {
    runtime("org.jasig.cas:cas-server-webapp:3.5.2@war") {
        transitive = true // setting this to true calculates transitive dependencies for addition to the target WAR
    }
}
```

Most other configuration is handled like the regular [Gradle WAR plugin](http://www.gradle.org/docs/current/userguide/war_plugin.html). There is one added convention:

```groovy
warOverlay {
    includeWarJars false // whether to include the jar files in the WAR. Default is false. If false, it might be useful to set transitive to `true` for the WAR dependency so its dependencies will be calculated and added
}
```

For a sample, see https://github.com/Unicon/unicon-cas-overlay/blob/CAS4/build.gradle
