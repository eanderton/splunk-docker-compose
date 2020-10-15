splunk-docker-compose
=====

An example project using Splunk and docker-compose.

The project utilizes docker-compose to create an isolated Splunk environment for testing
in a Docker container.
 
A sample Splunk application, `musicaldashboardtutorial`, is embedded in the repository,
as one would when performing splunk development. This is based on the online tutorial provided
Splunk: http://dev.splunk.com/view/webframework-tutorials/SP-CAAAEN2

Additionally, a distinct python container is used to lint and unit-test some of the code 
in the project during a build.  This is done to demonstrate how to isolate activities to 
distinct containers that may have different properties for specific tasks.

The automation script, `acdc` is used to run various different commands via `docker-compose`
in order to build and test the application against the Splunk container.  In a more involved
project, this script would contain more targets and might be replaced with either `paver`, `Make`,
or any number of other build automation tools.

To see the project in action, first install Docker and docker-compose.  Then launch a BASH shell,
and run the following command:

```
./acdc start build test
```

Splunk will be browsable via http://127.0.0.1:8000.  The Musical Dashbord app should be viewable 
under Apps.


When done, simply clean up the environment:
```
./acdc clean
```

This will destroy all containers associated with the project, and remove all intermediate files.


ACDC
-----

An 'automation control for docker-compose' script, `acdc` is provided in this project
to simplify routine docker-compose activities.  It also provides an environment-neutral way
to automate this example project by requiring nothing more than BASH.

To begin, launch a BASH shell using your native BASH, `git bash`, or the Windows Linux Subsystem.

ACDC provides online help to get you started.

```
Automation control for docker compose
Usage:
  ./acdc <command> [<command> ...]

Valid commands:
  help - shows this message
  start - start containers
  build - build software
  test - install and run software
  splunk - interactive splunk shell
  clean - cleans up environment
```
