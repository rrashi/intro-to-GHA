# Intro to Github Actions
A dummy repository to learn how to set up and use Github actions 😄
 
### Getting started
Github actions is a continuous integration and continuous delivery (C/CD) platforn that allows you to automate your build, test, and deployment pipeline. 



### Components
**Event:** A specfic activity in the repository that triggers a workflow run (eg. creating a pull-request)

**Workflows:** A configurable automated process that will run one or more jobs

**Jobs:** A set of steps in a workflow that is executed on the same runner

**Runner:** A server that runs your workflows when their triggered

**Actions:** A resuable, custom application that performs tasks required by multiple workflows

**Step:** Smallest component of a workflow, an individual task run within a job

<img width="794" alt="Screenshot 2023-08-08 at 2 24 21 PM" src="https://github.com/rrashi/learning-GHA-wooo/assets/61819683/7a72dbdb-b752-4c16-9f57-6b8374cc8743">

In summary, an *event* triggers a *workflow* which contains multiple *jobs* each of which run on independent servers called *runners*. Jobs are made up of *steps* which are tiny tasks and may contain calling a reusable *action*.
