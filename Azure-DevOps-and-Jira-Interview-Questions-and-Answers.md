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

1. Put the application code in a supported repository, such as Azure Repos Git or GitHub.
2. In the Azure DevOps project, open **Pipelines** and choose **New pipeline**.
3. Select the repository provider and authorize the connection if prompted.
4. Select the repository and configure the pipeline. You can start with a suggested template or write an `azure-pipelines.yml` file.
5. Define the trigger, agent pool, build steps, tests, and artifact publishing steps.
6. Save the YAML file in the repository and run the pipeline.
7. Review logs, fix failures, and verify that the expected artifact is produced.
8. For deployment, add stages and environments, configure service connections and permissions, and use approvals or checks for sensitive environments.

Keep credentials out of YAML and source code. Use protected variables, variable groups, or an appropriate secret store, and grant the pipeline only the permissions it needs.

## 8. How do you connect an Azure Repo to a pipeline?

In Azure DevOps, create a pipeline from **Pipelines → New pipeline → Azure Repos Git**, then select the project repository. Azure DevOps can add a YAML pipeline file to that repo. Choose a template or provide your own YAML, commit it, and run the pipeline.

If the pipeline already exists, configure its repository in the pipeline settings and check its YAML path and branch. Make sure the build-service identity has permission to read the repository. For deployment to Azure resources, also configure an Azure service connection; connecting the code repository alone does not grant deployment access.

## 9. What are common DevOps interview questions and answers?

### Q1. What is DevOps?

**Answer:** DevOps is a set of practices and a culture that brings development and operations teams together. It emphasizes automation, shared responsibility, continuous feedback, reliable releases, and improving the delivery lifecycle.

### Q2. What is the difference between continuous integration, continuous delivery, and continuous deployment?

**Answer:** Continuous integration (CI) frequently merges changes and automatically builds and tests them. Continuous delivery keeps validated changes ready for release, typically with a human approval before production. Continuous deployment automatically releases every change that passes the defined checks.

### Q3. What is a CI/CD pipeline?

**Answer:** It is an automated sequence of steps that takes a code change through activities such as checkout, build, tests, security checks, packaging, artifact publishing, and deployment.

### Q4. What is an artifact?

**Answer:** An artifact is a versioned output of a build, such as a package, compiled application, container image, or deployment bundle. The same tested artifact should be promoted between environments rather than rebuilt differently for each one.

### Q5. What is Infrastructure as Code (IaC)?

**Answer:** IaC defines infrastructure in version-controlled files so it can be reviewed, tested, and provisioned consistently. Examples include Terraform, Bicep, and Azure Resource Manager templates.

### Q6. What is a container?

**Answer:** A container is an isolated process packaged with its application and required dependencies. It uses the host operating system's kernel, which makes it generally lighter than a virtual machine.

### Q7. What is Docker?

**Answer:** Docker is a platform and ecosystem for building, distributing, and running containers. A Dockerfile describes how to build an image; a container is a running instance of an image.

### Q8. How do you investigate a failed deployment?

**Answer:** I would identify the failed stage and first failing step, inspect its logs and recent changes, and determine whether the failure is in the artifact, configuration, permissions, infrastructure, or application health. I would use a safe rollback or mitigation if necessary, then fix the cause and verify recovery.

### Q9. How do you protect secrets in a pipeline?

**Answer:** I would use a secret manager or protected pipeline variables, restrict access with least privilege, avoid printing secrets in logs, rotate credentials, and use short-lived identity-based authentication where supported.

### Q10. What is monitoring and why is it important?

**Answer:** Monitoring collects metrics, logs, traces, and alerts to show system health and user impact. It helps teams detect issues, troubleshoot them, and verify that a release is operating correctly.

### Q11. What is a rollback?

**Answer:** A rollback restores a previously known-good application version or configuration when a release causes problems. The rollback method should be tested, and data changes may require a separate forward-fix or recovery plan.

### Q12. What is a pull request?

**Answer:** A pull request proposes changes for review and integration. It supports collaboration through code review and automated checks such as builds, tests, and policy validation.

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

- Faster, more repeatable delivery through automation.
- Earlier feedback from builds, tests, and monitoring.
- Better collaboration and shared ownership across development and operations.
- More consistent environments when configuration and infrastructure are managed as code.
- Faster incident recovery when deployments, observability, and rollback procedures are well designed.

**Challenges**

- Requires investment in culture, skills, tooling, and ongoing maintenance.
- Poorly designed automation can spread mistakes quickly.
- Pipelines, permissions, and infrastructure add complexity and need security controls.
- Teams can over-focus on tool adoption instead of improving outcomes.
- Continuous delivery does not remove the need for testing, governance, or operational readiness.

## 12. Will DevOps interview questions help me if I have a B.E. and 1–2 years of experience?

Yes. Preparing these questions can help you explain your knowledge clearly, but interviewers also look for practical examples and an honest account of what you personally did. A B.E. degree and 1–2 years of experience can be relevant; neither guarantees a role by itself.

Be ready to describe a project end to end: the repository, branching or pull-request process, pipeline stages, tests, deployment environments, monitoring, a problem you solved, and what you learned. If you have only practiced a tool in a lab, say so rather than presenting it as production experience. Include DevOps skills on your resume only when you can explain and demonstrate them.

## 13. What is the role and importance of DevOps in full-stack development?

DevOps helps full-stack teams build, test, deploy, and operate both frontend and backend changes reliably. It can automate builds and tests, manage configuration and infrastructure, package applications, deploy services, and provide monitoring and feedback.

For example, a pipeline might run frontend unit tests, backend tests, and security checks; build versioned artifacts or container images; deploy to a test environment; and promote the validated release after approval. DevOps practices help full-stack developers understand how their changes behave in production and work more effectively with operations and platform teams.

## 14. What is the difference between Docker and a container? How do they help in DevOps?

**Docker** is a toolset and platform commonly used to create and run containers. A **container** is the isolated running application process. A Docker **image** is the packaged, read-only template from which containers are created.

Containers help DevOps by packaging an application and its dependencies consistently across development, test, and production. They can make environments more reproducible and deployments easier to automate. Containers are not full virtual machines: they share the host kernel, so teams still need to manage image security, resource limits, networking, persistent data, and host security.

## 15. What is the DevOps process, and what are typical Azure DevOps and GitOps architectures?

### Typical DevOps process

1. **Plan:** Define and prioritize work in a backlog.
2. **Code:** Make changes in version control and submit them for review.
3. **Build and test:** Run CI builds, automated tests, and appropriate quality or security checks.
4. **Package:** Publish a versioned artifact or container image.
5. **Release and deploy:** Deploy the artifact through environments, using approvals and checks where appropriate.
6. **Operate and observe:** Monitor health, logs, metrics, traces, and user impact.
7. **Learn and improve:** Use feedback and incidents to improve the product, automation, and process.

### Example Azure DevOps architecture

**Developer → Azure Repos → Azure Pipelines CI → tests and quality checks → versioned artifact in Azure Artifacts or a container registry → deployment stage(s) → target environments → monitoring and feedback**

Azure Boards can track work and link it to commits, pull requests, builds, and releases. Pipeline identities, service connections, permissions, and secrets should be configured securely.

### Example GitOps architecture

**Developer → application source in Git → CI builds/tests and publishes an image → deployment configuration in a Git repository is updated → GitOps controller watches the repository → controller reconciles the target cluster to the declared state → monitoring and feedback**

The Git repository records the desired deployment state. The controller detects drift and attempts to reconcile the environment. Changes are normally made through reviewed Git commits rather than manual edits to the live cluster. CI creates and validates artifacts; the GitOps controller handles continuous delivery and reconciliation.