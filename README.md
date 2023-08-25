# Intro to Github Actions
A dummy repository to learn some basic uses of Github actions 😄
 
## Getting started 
Github actions is a continuous integration and continuous delivery (CI/CD) platform that allows you to automate your build, test, and deployment pipeline. 
<br>
<br>
<details>
<summary> Theory </summary>
 
### Basic Components
  **Event:** A specfic activity in the repository that triggers a workflow run (eg. creating a pull-request)
  
  **Workflows:** A configurable automated process that will run one or more jobs
  
  **Jobs:** A set of steps in a workflow that is executed on the same runner
  
  **Runner:** A server that runs your workflows when their triggered
  
  **Step:** Smallest component of a workflow, an individual task run within a job
  
  **Actions:** A resuable, custom application that performs tasks required by multiple workflows
  
  <img width="794" alt="Screenshot 2023-08-08 at 2 24 21 PM" src="https://github.com/rrashi/learning-GHA-wooo/assets/61819683/7a72dbdb-b752-4c16-9f57-6b8374cc8743">
  
  In summary, an *event* triggers a *workflow* which contains multiple *jobs* each of which run on independent servers called *runners*. Jobs are made up of *steps* and may contain calling resuable *actions*.
  
  ### How it works
  
  Workflows are stored within `.github/workflows` in all repositories and are defined as YAML files. Composite actions can also be defined under a `.github/actions` directory. Github finds requried workflows within these directories and then based on how each workflow is triggered, executes them. All workflows can be found within the **Actions** tab in the repo. 
  Secrets and env variables per environment are stored in the settings. These can be on an environment, repository, or organization level.
  
  <img width="344" alt="Screenshot 2023-08-11 at 1 00 12 PM" src="https://github.com/rrashi/intro-to-GHA/assets/61819683/fbe0be90-e355-4de3-9d6c-5dadacb6cece">
  
  <img width="336" alt="Screenshot 2023-08-11 at 12 58 00 PM" src="https://github.com/rrashi/intro-to-GHA/assets/61819683/2ea74e78-ef76-4b29-9752-c4467f40a752">

  ### Communication between jobs and steps

 Parts of the workflow can communicate and share data. Github allows communication between steps using outputs generated through `$GITHUB_OUTPUT`. You can also use `$GITHUB_ENV` to save outputs and then access them in a later step using `env.{VARIABLE}` Because jobs run on different runners, comunication between them would require the creation of a dependency between the jobs. If job B requires an input from job A, the 2 jobs would have to run sequentially. By default, jobs run in parallel. This order is specified via a `needs` parameter in a dependent job (here, job B). 
  
  ### Composite actions vs workflows
  As mentioned earlier, actions are individual tasks that you can combine to create jobs and customize your workflow. There are pre-existing actions available on [Github Marketplace](https://github.com/marketplace?type=). However, we can also create our own. 
  
  While both workflows and composite actions are reusable, there's a difference between them
  
  | Workflows               | Composite Actions                            | 
  | :------:                | :------:                                     |
  | Can't be nested         | Can be nested                                | 
  | Can use secrets         | Can't use secrets (passed as inputs instead) |
  | Can be conditional      | Can't be controlled conditionally            |           
  
  
For more details, look at [3] in references

### Contexts 
Contexts are a way to access information about workflow runs, variables, runner environments, jobs, and steps. Each context is an object that contains properties, which can be strings or other objects. [4]

### Concurrency
Github allows useers to specify a `concurrency` variable that ensures only a single workflow or job is in progress. This is particularly useful in scenarios when we'd want only a single deployment in progress at a time (like for production environments). You can specify the concurrency using the `github` context.

 [**Jump to top**](#getting-started)

---
</details>


## Workflow basics
Goals:
- Understand the hierarchy of a workflow
- Understand the syntax of a workflow
- Know the differences between jobs, steps, and actions

Tasks:
1. Update the starter template workflow to be run on creating a pull request
2. Create a new job A that prints the statement “Hello world”
3. Commit and push
4. Open a PR for your branch and see the workflow run

## Secrets and Variables 
Goals:
- Understand how secrets and variables are accessed within a workflow
- Be able to pass data between steps of the same job
- Be able to Pass data between multiple jobs

Tasks:
1. Add a new step to job A that echoes the COOL_VARIABLE global repo variable 
2. Add another step that generates a random number and saves it as a github output
6. Add an output to job A that outputs the random number
7. Create a new job B that takes an input from job A
8. Echo the input received to job B

## Composite actions
Goals:
1. Understand the difference between a composite action and a workflow
2. Call pre-defined reusable actions
3. Define your own composite action and call it within your workflow

Tasks:
1. Add a new job in the workflow that calls a reusable (here's a [link](https://github.com/marketplace/actions/funny-comments) to an action that puts funny comments on your PR)
2. Create a new composite action that takes in an input string and echoes hello world
3. Replace the code in the workflow's job A to call the action instead

### References 
[1] Tutorial on YAML: https://learnxinyminutes.com/docs/yaml/

[2] Workflow syntax: https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions

[3] Resuable workflows vs composite actions: https://dev.to/n3wt0n/composite-actions-vs-reusable-workflows-what-is-the-difference-github-actions-11kd

[4] Contexts https://docs.github.com/en/actions/learn-github-actions/contexts#github-context
