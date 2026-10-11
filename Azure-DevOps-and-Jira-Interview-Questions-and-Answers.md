# Azure DevOps, Jira, and DevOps Interview Questions and Answers

This guide covers Agile work-tracking tools, Azure DevOps pipelines, GitOps, containers, and common DevOps interview topics.

> **Terminology note:** This guide interprets “tellor” as **Trello**, “spice” as **spike**, and “performance board” as a **work board** (such as an Azure Boards Kanban board). Team terminology and workflow states can be customized.

## 1. What is Azure Boards?

**Answer:** Azure Boards is a work-tracking service within Microsoft Azure DevOps. It helps development teams plan, assign, track, and manage their work.

**Key features:**

- Work-item tracking
- Agile boards and Kanban boards
- Sprint planning and backlogs
- Bug tracking
- Progress monitoring through charts and dashboards

**Example:** A developer receives a task to fix a login-page bug. The team creates a work item in Azure Boards, assigns it to the developer, and tracks its progress until completion.

## 2. What is Jira?

**Answer:** Jira is a project management and issue-tracking tool developed by Atlassian. It is widely used by Agile teams to manage tasks, bugs, user stories, and sprints.

**Key features:**

- Scrum and Kanban boards
- Sprint planning
- Bug and issue tracking
- Task assignment
- Reports and project progress tracking

**Example:** A Scrum team uses Jira to create user stories, assign tasks to developers, track bugs, and monitor sprint progress.

## 3. What is Trello?

**Answer:** Trello is a visual work-management and project-management tool developed by Atlassian. It helps teams organize tasks and track progress using boards, lists, and cards.

**Key features of Trello:**

- **Boards:** Represent a project or workflow.
- **Lists:** Represent stages of work, such as To Do, In Progress, and Done.
- **Cards:** Represent individual tasks. Cards can have descriptions, due dates, checklists, and assignments.
- **Collaboration:** Lets team members share updates and track progress.

**Example:** A software development team creates a Trello board to manage a website project.

## 4. What is the difference between an Epic, Feature, User Story, Spike, Issue, Task, and Bug?

**Answer:** These terms describe different types of work items used in Agile project management. Their exact order can depend on the tool and the team's process.

| Work item | Meaning | Example |
|---|---|---|
| **Epic** | A large business goal that can be split into smaller items. | Online shopping system |
| **Feature** | A major ability or part of a product. | Online payment |
| **User Story** | A requirement written from the user's point of view. | As a customer, I want to pay online. |
| **Task** | A specific piece of work. | Connect the payment service. |
| **Bug** | Something in the product that does not work as expected. | Payment fails after clicking Pay. |
| **Spike** | A short, time-limited investigation to learn more before deciding what to do. | Research payment options. |
| **Issue** | A general work item or problem. Its meaning depends on the tool and team. | Investigate a deployment failure. |

A common hierarchy in Azure Boards is:

**Epic → Feature → User Story / Product Backlog Item → Task**

Bugs and spikes can be tracked at different levels, depending on the team's setup. Jira uses issue types that teams can configure, and commonly supports relationships such as **Epic → Story, Task, or Bug**.

## 5. What are the different statuses of work items in Azure Boards and Jira?

**Answer:** Statuses show the current stage of a work item. The available statuses depend on the workflow and project setup.

| Status | Meaning |
|---|---|
| **New / To Do** | Work has not started. |
| **Active / In Progress** | Someone is working on it. |
| **Resolved** | A solution has been made, or the item is waiting to be checked. The exact meaning depends on the workflow. |
| **In Review** | The work is being reviewed. |
| **Ready for Testing** | The work is ready for testing. |
| **Closed / Done** | The work is considered complete. |
| **Blocked** | Work cannot continue because of a problem or delay. |

**Example workflow:**

**New / To Do → Active / In Progress → In Review / Testing → Closed / Done**

**Interview tip:** Not every board has the same statuses. Azure Boards can have different states for different types of work items. Jira workflows can also be changed to fit a team's needs.

## 6. What is Azure DevOps, and what are pipelines?

**Answer:** Azure DevOps is a Microsoft platform that provides tools for planning, developing, testing, and delivering software.

Its main services include:

- **Azure Boards:** Plan and track work.
- **Azure Repos:** Store and manage source code using Git.
- **Azure Pipelines:** Build, test, and release applications automatically.
- **Azure Test Plans:** Plan and run tests.
- **Azure Artifacts:** Store and share software packages.

**What is a pipeline?**

A pipeline is a set of automatic steps that builds, tests, and releases an application.

**Example:** When a developer adds code to a Git repository, a pipeline can build the application, run tests, and release it if it passes the required checks.

## 7. How do you create a pipeline?

**Answer:** I can create a pipeline by following these steps:

**Step 1: Create a project**

Sign in to Azure DevOps and create a new project.

**Step 2: Add source code**

Create or import a Git repository using Azure Repos, or connect a supported external repository.

**Step 3: Create a pipeline**

Open **Pipelines**, select **New pipeline**, and choose the repository and setup method.

**Step 4: Configure YAML**

Add the build, test, and release steps to an `azure-pipelines.yml` file.

**Step 5: Run and monitor**

Save the pipeline, run it, and check the logs and test results.

A simple example for a Python project is:

```yaml
trigger:
  - main

pool:
  vmImage: ubuntu-latest

steps:
  - task: UsePythonVersion@0
    inputs:
      versionSpec: '3.12'

  - script: |
      python -m pip install --upgrade pip
      pip install -r requirements.txt
    displayName: 'Install dependencies'

  - script: |
      python -m pytest
    displayName: 'Run tests'
```

This pipeline runs when changes are pushed to `main`, installs Python packages, and runs tests. It expects the repository to have a `requirements.txt` file and tests that can run with pytest.

## 8. How do you connect Azure Repos to Azure Pipelines?

**Answer:** Azure Repos and Azure Pipelines are both services in Azure DevOps and can be connected directly.

**Steps:**

1. Create a project in Azure DevOps.
2. Open **Repos** and create or import a Git repository.
3. Add your source code to the repository.
4. Open **Pipelines → New pipeline**.
5. Select **Azure Repos Git**.
6. Choose your repository.
7. Set up the pipeline using YAML or a template.
8. Save and run the pipeline.
9. Set a trigger so code changes start the pipeline automatically.

**Example:** When a developer pushes code to the `main` branch, Azure Pipelines can build the application and run tests automatically.

For releases to other services, you may also need service connections, permissions, and login details.

## 9. What are common DevOps interview questions and answers?

Here are some important questions to prepare.

### Q1. What is DevOps?

DevOps brings development and operations teams together. They work as a team and use automation to release software more often and with fewer problems.

### Q2. What is CI/CD?

- **CI — Continuous Integration:** Regularly add code changes and automatically build and test them.
- **CD — Continuous Delivery or Continuous Deployment:** Automatically prepare software for release or release it.

With **Continuous Delivery**, a person usually approves the release to production. With **Continuous Deployment**, changes that pass the checks are released to production automatically.

### Q3. What is the difference between Git and GitHub?

Git tracks changes to code. GitHub is a website that stores Git projects and helps people work together, review code, and share changes.

### Q4. What is a Docker container?

A Docker container runs an app with the files it needs. It helps the app work in a similar way on different computers.

### Q5. What is Infrastructure as Code (IaC)?

Infrastructure as Code means setting up things like servers and networks using files instead of doing every step by hand. Terraform and Azure Bicep are examples.

### Q6. What is Jenkins?

Jenkins is a tool that can build, test, and release software automatically.

### Q7. What is Kubernetes?

Kubernetes is a tool for running and managing containers. It can start apps, add more copies when needed, and restart them if they stop working.

### Q8. What is monitoring in DevOps?

Monitoring checks whether an app and its systems are working well. It can show errors, speed, and availability. Azure Monitor and Prometheus are examples of monitoring tools.

### Q9. What is a rollback?

A rollback means returning to an earlier version that worked when a new release causes problems.

### Q10. What is the difference between Agile and DevOps?

Agile focuses on building software in small steps, getting user feedback, and making changes. DevOps focuses on helping teams build, test, release, and run software together. Agile and DevOps can be used together.

## 10. What is the difference between Azure DevOps and GitOps?

They are not direct alternatives: **Azure DevOps is a product suite**, while **GitOps is an operating and delivery approach**.

| Azure DevOps | GitOps |
|---|---|
| A Microsoft platform with services for planning, repositories, pipelines, testing, and artifacts. | A practice in which Git is the source of truth for desired system and application state. |
| Can run CI and CD workflows and can support GitOps-based deployments. | Commonly uses a controller, such as Flux or Argo CD, to observe Git and reconcile a running environment to the declared state. |
| Pipelines may push deployments to target environments. | A reconciliation agent commonly pulls the desired configuration from Git and applies changes. |

A team can use Azure Repos and Azure Pipelines for CI and still use GitOps tooling for deployment. GitOps is especially common for Kubernetes, but the core principle is version-controlled desired state and continuous reconciliation.

## 11. What are the advantages and disadvantages of DevOps?

**Advantages**

1. Faster software delivery through automation.
2. Better teamwork between development and operations.
3. Bugs can be found early through automatic testing.
4. Releases can be more consistent.
5. It is easier to grow and manage systems.
6. Teams can get feedback and fix problems sooner.

**Disadvantages**

1. The first setup can be difficult.
2. Tools, computers, and training need time and money.
3. A mistake in automation can spread quickly.
4. Passwords and access must be kept safe.
5. Pipelines need regular care and checks.
6. Changes to the way a company works can take time.

**Interview answer:** DevOps helps teams release software faster and work better together. To do it well, teams need the right skills, safe ways to manage access, and regular care of their tools and pipelines.

## 12. Will mentioning DevOps on my resume help me get a job with a B.E. degree and 1–2 years of experience?

**Answer:** Yes. DevOps skills can help you apply for suitable jobs, but your resume should only list skills and experience you really have.

A B.E. degree in Computer Science or a related subject can give you a useful start. For jobs that ask for 1–2 years of experience, employers often want to know what tools and work processes you have used.

For a junior DevOps job, learn about:

- Linux and computer networks.
- Git and GitHub.
- Azure DevOps and YAML pipelines.
- Docker and containers.
- Cloud basics, such as Azure or AWS.
- Writing simple scripts with Python or Bash.
- Finding and fixing problems, and checking systems.

**Important:** If you have 1–2 years of work experience, describe your real duties and results. If you have only practiced through lessons or personal projects, list those under skills or projects instead of calling them professional experience.

**Beginner project idea:** Build a small Python app, store it in Git, use Azure Pipelines to run tests, package it with Docker, and explain the steps in your GitHub project.

## 13. What is the role and importance of DevOps in full-stack development?

**Answer:** DevOps helps full-stack developers build, test, release, and check both the frontend and backend of an app.

For example, a web app might have a React frontend, a Python backend, and a database. DevOps can help by:

- Building the frontend and backend automatically.
- Running tests before release.
- Setting up development, test, and live environments.
- Using Docker to package backend apps.
- Releasing apps to cloud services.
- Checking app errors and speed.
- Keeping settings and passwords safe.

**Example workflow:**

```text
Frontend: React / HTML / CSS
Backend: Python / Node.js / Java
Database: MySQL / PostgreSQL
Git → CI/CD pipeline → Tests → Docker / Cloud release → Monitoring
```

DevOps reduces manual release work and helps teams release full-stack apps in a steady and reliable way.

## 14. What is the difference between Docker and a container, and how do they help in DevOps?

**Answer:** Docker is a set of tools for building and running containers. A container runs an app together with the files it needs.

| Docker | Container |
|---|---|
| Provides tools for working with containers. | Is a running app in an isolated environment. |
| Builds images and starts containers. | Runs the app packaged in an image. |
| Includes tools such as Docker Engine and Docker CLI. | Uses features of the operating system to keep apps separate. |
| Helps package apps in a standard way. | Helps apps run in a similar way in different places. |

**Example:** A developer packages a Python app and its libraries into a Docker image. They can start a container from that image on their computer or on a compatible server.

**How Docker helps in DevOps:**

- Apps can run in a similar way during development and after release.
- Docker can be used in automatic build and release pipelines.
- Apps can be packaged and released more easily.
- Apps are kept separate from each other.
- Apps can be scaled using tools such as Kubernetes.

**Remember:** Docker is not the same as a container. Docker provides tools to build and manage containers.

## 15. What is the DevOps process, how does it work, and what are the architectures of Azure DevOps and GitOps?

**Answer:** The DevOps process is a continuous cycle of planning, coding, building, testing, releasing, deploying, running, and monitoring software.

### A. General DevOps lifecycle

```text
Plan               → Code              → Build
Jira / Azure Boards  Git / Azure Repos   Azure Pipelines / Jenkins
                                           ↓
Monitor            ← Deploy            ← Test
Logs / Metrics       Cloud / Containers  Automated tests
     └──────────── Feedback helps plan the next changes ────────────┘
```

### B. Azure DevOps architecture

Azure DevOps can coordinate work across these services:

```text
Azure Boards
Planning and work tracking
      ↓
Azure Repos
Source code and version control
      ↓
Azure Pipelines
Build, test, and release automation
      ↓
Deployment environment
Azure, other clouds, servers, or Kubernetes
      ↓
Monitoring and feedback
Logs, metrics, alerts, and new work items
```

This is a simple view of how the services can work together, not a required order. Azure Artifacts can store packages, and Azure Test Plans can help manage tests.

### C. GitOps architecture

GitOps stores the wanted setup for an application or its infrastructure in Git. A GitOps tool keeps checking the running environment and compares it with the setup in Git.

```text
Developer / CI pipeline
Build and test application image
          ↓
Git repository
Versioned YAML and desired setup
          ↓
GitOps controller
Argo CD or Flux checks Git and applies changes
          ↓
Kubernetes cluster
Runs the application using the setup in Git
```

**Example:** A setup file says the application should have two copies running. A developer changes the number to three. The GitOps controller sees the change and works to make the cluster run three copies.

**Key difference:** Azure DevOps can automate the overall software delivery process. GitOps focuses on keeping an environment in the state described in Git. Teams can use both together.