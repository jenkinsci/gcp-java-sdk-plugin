# Google Cloud Platform SDK Plugin

This plugin provides the [Java Cloud Client Libraries](https://cloud.google.com/java/docs/reference) from [Google Cloud SDK](https://cloud.google.com/sdk/) as a library to be used by other plugins.

This use single version for all modules following `${revision}-${changeList}` pattern.
The `revision` part is aligned with [Google Java Cloud BOM version](https://github.com/googleapis/java-cloud-bom).
```
io.jenkins.plugins:gcp-java-sdk:26.23.0-999999-SNAPSHOT

    io.jenkins.plugins:gcp-java-sdk-auth:26.23.0-999999-SNAPSHOT
      | com.google.auth:google-auth-library-oauth2-http:1.19.0
      | com.google.auth:google-auth-library-credentials:1.19.0
      | com.google.auth:google-auth-library-appengine:1.19.0

    io.jenkins.plugins:gcp-java-sdk-storage:26.23.0-999999-SNAPSHOT
      | com.google.cloud:google-cloud-storage:2.27.0
```

:bulb: This plugin does not provide all of the [Java Cloud Client Libraries](https://cloud.google.com/java/docs/reference), but only the ones which were requested by other plugins, following an incremental and iterative approach. If you need a particular library that is not yet provided by this plugin, please feel free to request it or contribute it.

## Plugins 

### gcp-java-sdk-*

Contains an individual [Java Cloud Client Libraries](https://cloud.google.com/java/docs/reference) module with the same name.

## Adding a new plugin 

If you need to use an API that is not yet published as its own plugin, feel free to submit a Pull Request to create a plugin for it. 

* Create a new directory `gcp-java-sdk-<name>`. The `name` should be identical to the [Java Cloud Client Libraries](https://cloud.google.com/java/docs/reference) module.
* Create `pom.xml`.
  * Depend on `com.google.cloud:google-cloud-<name>`. The name should be identical to the Google SDK module.
  * Transitive dependencies should be replaced by their equivalent plugin dependency.
  * Create `src/main/resources/index.jelly`. Look at existing modules to have a similar description.
  * Add the module to the root `pom.xml`.

