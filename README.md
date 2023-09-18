# Google Cloud Platform SDK Plugin

This plugin provides the [Java Cloud Client Libraries](https://cloud.google.com/java/docs/reference) from [Google Cloud SDK](https://cloud.google.com/sdk/) as a library to be used by other plugins.

Because there are no unified versions in Google clients, all modules will have different versions, matching the version of the client module they refer to.

Commonly used modules have their own plugins. A general `gcp-java-sdk` module provides [google-cloud-java](https://github.com/googleapis/google-cloud-java) as a library.

:bulb: This plugin does not provide all of the [Java Cloud Client Libraries](https://cloud.google.com/java/docs/reference), but only the ones which were requested by other plugins, following an incremental and iterative approach. If you need a particular library that is not yet provided by this plugin, please feel free to request it or contribute it.

## Plugins 

### gcp-java-sdk

Library plugin for [google-cloud-java](https://github.com/googleapis/google-cloud-java) which is the global Google Cloud Client Library for Java. It is heavyweight.

### gcp-java-sdk-*

Contains an individual [Java Cloud Client Libraries](https://cloud.google.com/java/docs/reference) module with the same name.

## Adding a new plugin 

If you need to use an API that is not yet published as its own plugin, feel free to submit a Pull Request to create a plugin for it. This will avoid pulling the all-in-one `gcp-java-sdk` plugin.

* Create a new directory `gcp-java-sdk-<name>`. The `name` should be identical to the [Java Cloud Client Libraries](https://cloud.google.com/java/docs/reference) module.
* Create `pom.xml`.
  * Depend on `com.google.cloud:google-cloud-<name>`. The name should be identical to the Google SDK module.
  * Transitive dependencies should be replaced by their equivalent plugin dependency.
  * Create `src/main/resources/index.jelly`. Look at existing modules to have a similar description.
  * Add the module to the root `pom.xml`.

