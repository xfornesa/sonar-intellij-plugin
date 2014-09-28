SonarQube IntelliJ Community Plugin
===================================

The main goal of this plugin is to show [SonarQube](http://sonarqube.org) issues directly from within the IntelliJ IDE.
This plugin is build to work in IntelliJ IDEA, RubyMine, WebStorm, PhpStorm, PyCharm, AppCode or Android Studio and for any programming language you use in these IDE that SonarQube can analyze.
Two tasks are covered by the plugin: 
* downloading already analyzed code from sonar server and show them in the IDEA
* running a local analysis script and analyze new issues

If you have any issues using the plugin, please let us know by [filing a new issue](https://github.com/sonar-intellij-plugin/sonar-intellij-plugin/issues/new), contacting us via the [Google Groups mailing list](https://groups.google.com/forum/#!forum/sonarqube-intellij-plugin) or even sending a pull request. Thanks for your support.


### Usage

#### Project Configuration

After the installation you first of all need to configure the connection to your sonar server. This is done per project and/or module. You can use a remote server or a local one on your machine, depends on how you work with sonar.

Go to `File -> Settings (Ctrl+Alt+S)-> SonarQube`. 

![alt text][serverSelection]
[serverSelection]: https://raw.github.com/sonar-intellij-plugin/sonar-intellij-plugin/sonar_4/screenshots/server_selection.png "Example server selection"

Click Add and configure sonar server

![alt text][serverConfiguration]
[serverConfiguration]: https://raw.github.com/sonar-intellij-plugin/sonar-intellij-plugin/sonar_4/screenshots/server_configuration.png "Example server configuration"

Select the sonar resource

![alt text][resourceSelection]
[resourceSelection]: https://raw.github.com/sonar-intellij-plugin/sonar-intellij-plugin/sonar_4/screenshots/resource_selection.png "Example resource selection"

The finished sonar server configuration should look like:

![alt text][serverConfigurationComplete]
[serverConfigurationComplete]: https://raw.github.com/sonar-intellij-plugin/sonar-intellij-plugin/sonar_4/screenshots/server_configuration_complete.png "Example resource selection"

#### Local analysis configuration

After the configuration of the sonar server you are ready to start downloading issues and showing them in the IDE. But as soon you start editing your source code, you might want to trigger a local sonar analysis. To achieve this by using the plugin and showing new issues directly inside the IDE you need to tell the plugin how to analyse your project and provide the path to the sonar-report.json file. The plugin understands the contet of that report file and shows the result in the IDE.
Before configuring the plugin, you need to understand how to run local analysis for your project. 

Go to your prefered console and try to run depending on your project something like:

```
mvn sonar:sonar -DskipTests=true -Dsonar.language=java  -Dsonar.analysis.mode=incremental -Dsonar.host.url=http://localhost:9000
```

or

```
sonar-runner -Dsonar.analysis.mode=incremental -Dsonar.issuesReport.html.enable=true -Dsonar.host.url=http://localhost:9000
```

or
```
your_custom_script_to_perform_local_analysis.sh
```

After the script is done, your should see something like:

```
[INFO] [18:29:26.380] Export results to /path/to/your/project/target/sonar/sonar-report.json
[INFO] [18:29:26.383] Store results in database
[INFO] [18:29:26.500] ANALYSIS SUCCESSFUL
[INFO] [18:29:26.501] Executing post-job class org.sonar.issuesreport.ReportJob
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
```

**NOTE: The configuration of the local analysis is out of the scope of the plugin, please read the SonarQube documation about how to perform it**

TBD
