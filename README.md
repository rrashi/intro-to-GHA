# Intro to Github Actions
A dummy repository to learn some basic uses of Github actions 😄
 
## Getting started [TO-DO]
Github actions is a continuous integration and continuous delivery (C/CD) platforn that allows you to automate your build, test, and deployment pipeline. 


### Basic Components
**Event:** A specfic activity in the repository that triggers a workflow run (eg. creating a pull-request)

**Workflows:** A configurable automated process that will run one or more jobs

**Jobs:** A set of steps in a workflow that is executed on the same runner

**Runner:** A server that runs your workflows when their triggered

**Actions:** A resuable, custom application that performs tasks required by multiple workflows

**Step:** Smallest component of a workflow, an individual task run within a job

<img width="794" alt="Screenshot 2023-08-08 at 2 24 21 PM" src="https://github.com/rrashi/learning-GHA-wooo/assets/61819683/7a72dbdb-b752-4c16-9f57-6b8374cc8743">

In summary, an *event* triggers a *workflow* which contains multiple *jobs* each of which run on independent servers called *runners*. Jobs are made up of *steps* which are tiny tasks and may contain calling a resuable *action*.

### How it works

Workflows are stored within `.github/workflows` in all repositories and are defined as YAML files. Composite actions can also be defined under a `.github/actions` directory

<img width="364" alt="Screenshot 2023-08-09 at 2 52 43 PM" src="https://github.com/rrashi/intro-to-GHA/assets/61819683/d7ebbcbd-bd55-46df-9c66-1d20644f02d6">

Github finds requried workflows within these directories and then based on how each workflow is triggered, executes them in order. All workflows can be found within the **Actions** tab in the repo

<img width="326" alt="Screenshot 2023-08-09 at 3 05 14 PM" src="https://github.com/rrashi/intro-to-GHA/assets/61819683/9d328441-3a15-4fca-820b-41709a002aa5">

Secrets and env variables per environment are stored in the settings. These can be on an environment, repository, or organization level.

### Composite actions vs workflows [TO-DO]
i.e what goes under `/workflows` and what goes under `/actions`

For more details, look at [3] in references





## How to use this repo

This repository will be used to do some basic workflow and actions writing. To segregate the workflows, each person who clones the repo will have to branch off the main branch with a prefix that begins with ROUT-{your-name}, for example ROUT-gyoza. Within the workflows directory, you will find a starter workflow template with some guiding comments. The goals of the repository are the following:

1. Define a main workflow that is triggered on creating a pull request
2. Define a reusable action that echos the statement "Hello world"
3. Define a job that calls the reusable action within your main workflow
4. Go to the settings tab of the repository and add a new env variable under your name
5. Define another job that accesses and echos the newly defined variable in your workflow

Listed under the resoures section is a link to the github actions documentation which has more thorough information

### References 
[1] Tutorial on YAML: https://learnxinyminutes.com/docs/yaml/

[2] Workflow syntax: https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions

[3] Resuable workflows vs composite actions: https://dev.to/n3wt0n/composite-actions-vs-reusable-workflows-what-is-the-difference-github-actions-11kd
