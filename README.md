# Selenium---Jenkinsfile

selenium-pipeline
Run your Selenium Test using this declarative pipeline.

Pre-requisites.
Before we start you need to:

Have a Jenkins Instance with an admin user.
Have the browser you are going to use installed on your server (this pipeline do not use Docker for now!)
Have a maven project with your test code.
Also, you need to review the pipeline and check the path of the following variables:

JOB_FILES_DIRECTORY: This parameter set the Directory of the files in the workspace. The current value is: "${workspace}"+"/src/test/resources/files".
SUITE_NAME: This parameter set the suite name and path. The current value is: "src/test/resources/suites/"+"${JOB_SELENIUM_SUITE}"+".xml".
Selenium Test Stage: On this stage, if the test failed, you need to check the path where the screenshot are saved. The current value is: "**/screenshot/*.png".
SonarQube Stage: In order to be able to run Sonar on your test code, you need to define the Sonarqube server on your POM.xml.
Configure your Jenkins Job.
Create a Pipeline Job.
First, you need to install the pipeline plugins on Jenkins to be able to create a Pipeline job. Once you have installed all the plugins you need, you need to create a new job:

Left Menu -> New Item -> Add job title -> Select Pipeline.

Add parameters to the job execution.
On the Jenkins job, you need to add several parameters by clicking the option This project is parameterized:

JOB_GIT_URL: Code Repository URL (String Parameter)
JOB_GIT_BRANCH: Branch to download the project code to. You can add one or several branches (Choice Parameter)
JOB_GIT_CREDENTIAL: You need to define the user to download the project. You can fill this parameter using the users defined on your Jenkins System Credential. (Credentials Parameter)
JOB_OS: Operative System in which you are going to launch the Tests. You can add several OS such as Windows, Linux or MacOSX (Choice Parameter).
JOB_BROWSER: Browser in which you are going to launch the Tests. You can add several Browsers, such as Firefox, Internet Explorer or Chrome (Choice Parameter)
JOB_SELENIUM_SUITE: Name of the Test Suite to execute. You can add several test suites, for example acceptance or regression. (Choice Parameter)
JOB_ENABLE_SONAR: Variable to define if the code could be analyzed by Sonarqube. The Sonar Server should be defined on the POM. (Boolean Parameter)
Configure the pipeline section.
On the pipeline section of the job you need to set this repository:

URL: https://github.com/estefafdez/selenium-pipeline.git
Credentials: you do not need it. This is a public repository.
Branch: master (There is only one for now!)
Script Path: selenium-pipeline.jenkinsfile
Save the Job and click on RUN!
When your pipeline job is ready and all the parameters are set and filled, you just need to click on play and enjoy!
