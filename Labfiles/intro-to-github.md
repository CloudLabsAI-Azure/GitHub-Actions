# Getting Started with GitHub (Optional: Read-Only)

### Estimated Duration : 45 mins

### What is GitHub? 

**GitHub** is a cloud-based platform that uses Git, a distributed version control system, at its core. The GitHub platform simplifies the process of collaborating on projects and provides a website, command-line tools, and overall flow that allows developers and users to work together.

As you learned earlier, GitHub provides an AI-powered developer platform to build, scale, and deliver secure software. Let’s break down each one of the core pillars of the GitHub Enterprise platform: AI, Collaboration, Productivity, Security, and Scale.

### Benefits of using GitHub

1. **Collaboration:** GitHub makes it easy for multiple developers to work together on a project, regardless of their physical location. With features like branches, pull requests, and code reviews, teams can work in parallel without interfering with each other's work.

2. **Version Control:** Every change made to a project is tracked and recorded, making it easy to revert to previous versions if needed. This history of changes is valuable for understanding how a project has evolved.

3. **Community and Open Source:** GitHub hosts millions of open-source projects. Developers can contribute to these projects, learn from each other, and showcase their work to the global developer community.

4. **Integration:** GitHub integrates with numerous tools and services, from continuous integration and deployment (CI/CD) to project management and code review tools, streamlining the development workflow.

## Key features of GitHub

1. **What is a repository?**
    
    - A repository contains all of your project's files and each file's revision history. It is one of the essential parts that helps you collaborate with people. You can use repositories to manage your work, track changes, store revision history, and work with others. Before we dive too deep, let’s first start with how to create a repository.

2. **What are branches?**
   
   - **Purpose of Branches:**

      Branches allow for isolated development of features, fixes, or experiments without affecting the main codebase.

   -  **Safe Development:**

      Provide a safe environment to make changes. Mistakes can be reverted or corrected without impacting the main branch.

   -  **Merging into Production:**

      Changes in branches are merged into the default (main/production) branch only after being tested and verified. This ensures that the production code remains stable and reliable.

3. **What are commits?**

   - A **commit** is a change to one or more files on a branch. Every time a commit is created, it's assigned a unique ID and tracked, along with the time and contributor. Commits provide a clear audit trail for anyone reviewing the history of a file or linked item, such as an issue or pull request.
    
   ![](../media/2-commits.png)
   
     - Within a git repository, a file can exist in several valid states as it goes through the version control process:
     - The primary states for a file in a Git repository are:
     - **Untracked**: An initial state of a file when it isn't yet part of the Git repository. Git is unaware of its existence.
     - **Tracked**: A tracked file is one that Git is actively monitoring. It can be on one of the following substrates:
     - **Unmodified**: The file is tracked, but it hasn't been modified since the last commit.
     - **Modified**: The file has been changed since the last commit, but these changes aren't yet staged for the next commit.
     - **Staged**: The file has been modified, and the changes have been added to the staging area (also known as the index). These changes are ready to be made (committed).
     - **Committed**: The file is in the repository's database. It represents the latest committed version of the file.

These states and substates are important to collaborating with your team to know where each and every commit is in the process of your project.

4. **What are pull requests?**

   - A pull request is a mechanism used to signal that the commits from one branch are ready to be merged into another branch.The team member submitting the pull request requests one or more reviewers to verify the code and approve the merge. These reviewers have the opportunity to comment on changes, add their own, or use the pull request itself for further discussion. Once the changes have been approved (if approval is required), the pull request's source branch (the compare branch) is merged into the base branch.

     ![](../media/2-pull-request.png)

     #### The GitHub flow
   
     ![](../media/2-branching.png)

     - The GitHub flow can be defined as a lightweight workflow that allows for safe experimentation. You can test new ideas and collaborate with your team by using branching, pull requests, and merging. Now that we know the basics of GitHub, we can walk through the GitHub flow and its components.

     **i.** The first step of the GitHub flow is creating a branch so that the changes, features, and fixes you create don't affect the main branch. <br/>

     **ii.** The second step is to make your changes. We recommend deploying changes to your feature branch before merging into the main branch. Doing so ensures the changes are valid in a production environment. <br/>
     
     **iii.** The third step is to create a pull request to ask collaborators for feedback. Pull request review is so valuable that some repositories require an approval review before pull requests can be merged. <br/>
     
     **iv.** Next is the fourth step of reviewing and implementing your feedback from your collaborators. <br/>
     
     **v.** The fifth step: once you’re feeling great about your changes, now it's time to get your pull request approved and merge it into the main branch. <br/>
     
     **vi.** The sixth and final step is to delete your branch. Deleting your branch signals that your work on the branch is complete and prevents you or others from accidentally using old branches. <br/>

And that’s it; you’ve been through a GitHub flow cycle!

5. **Forking:** Forking is copying a repository from one user’s account to another. It allows you to freely experiment with changes without affecting the original project.

6. **GitHub Issues:** Issues are a way to track enhancements, tasks, and bugs for your projects. They help you manage and prioritize work, discuss ideas, and keep track of tasks.

### How do GitHub Actions automate development tasks?

#### GitHub decreases the time from idea to deployment.

GitHub is designed to help teams of developers and DevOps engineers build and deploy applications quickly. There are many features in GitHub that enable this, but they generally fall into one of two categories:

- **Communication:** Consider all of the ways that GitHub makes it easy for a team of developers to communicate about the software development project: code reviews in pull requests, GitHub issues, project boards, wikis, notifications, and so on.
  
- **Automation:** GitHub Actions lets your team automate workflows at every step in the software development process, from integration to delivery to deployment. It even lets you automate adding labels to pull requests and checking for stale issues and pull requests.

#### Use workflow automation to decrease development time.

We'll focus on automation in this module, so let's take a moment to understand how teams can use automation to reduce the amount of time it takes to complete a typical development and deployment workflow.

Consider all of the tasks that must happen after the code is written but before you can reliably use the code for its intended purpose. Depending on your organization's goals, you'll likely need to perform one or more of the following tasks:

- Ensure the code passes all unit tests.
- Perform code quality and compliance checks to make sure the source code meets the organization's standards.
- Check the code and its dependencies for known security issues.
- Build the code, integrating new sources from (potentially) multiple contributors.
- Ensure the software passes integration tests.
- Use a version of the new build.
- Deliver the new binaries to the appropriate filesystem location.
- Deploy the new binaries to one or more servers.
- If any of these tasks don't pass, report the issue to the proper individual or team for resolution.

### What are GitHub Actions?

GitHub Actions are packaged scripts designed to automate tasks within a software development workflow on GitHub. These actions can be configured to trigger complex workflows that meet your organization's specific needs. They can be set off whenever developers check new source code into a particular branch, at scheduled intervals, or manually. This results in a reliable and sustainable automated workflow, significantly reducing development time.

For more details, you can visit this link: [Introduction to GitHub](https://learn.microsoft.com/en-us/training/modules/introduction-to-github/)


### Workflow Syntax for GitHub Actions

- **Name**: The name of the workflow. GitHub displays the names of your workflows under your repository's "Actions" tab. If you omit the name, GitHub displays the workflow file path relative to the root of the repository.

- **Run-Name**: The name for workflow runs generated from the workflow. GitHub displays the workflow run name in the list of workflow runs on your repository's "Actions" tab. If the run name is omitted or is only whitespace, then the run name is set to event-specific information for the workflow run. For example, for a workflow triggered by a **push** or **pull_request** event, it is set as the commit message or the title of the pull request.

  - This value can include expressions and can reference the GitHub and input contexts.

  - Example of run-name:
  
    ```
    run-name: Deploy to ${{ inputs.deploy_target }} by @${{ github.actor }}
    ```

- **On**: To automatically trigger a workflow, use on to define which events can cause the workflow to run. For a list of available events, see "[Events that trigger workflows](https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows)."

  - You can define single or multiple events that can trigger a workflow or set a time schedule. You can also restrict the execution of a workflow to only occur for specific files, tags, or branch changes. These options are described in the following sections:

    - **Using a single event**: For example, a workflow with the following on-value will run when a push is made to any branch in the workflow's repository:

      ```
      on: push
      ```

    - **Using multiple events**: You can specify a single event or multiple events. For example, a workflow with the following value will run when a push is made to any branch in the repository or when someone forks the repository:

      ```
      on: [push, fork]
      ```

  - If you specify multiple events, only one of those events needs to occur to trigger your workflow. If multiple triggering events for your workflow occur at the same time, multiple workflow runs will be triggered.

- **Using activity types**: Some events have activity types that give you more control over when your workflow should run. Use `on.<event_name>.types` to define the type of event activity that will trigger a workflow run.

  - For example, the `issue_comment` event has the `created, edited, and deleted` activity types. If your workflow triggers the `label` event, it will run whenever a label is created, edited, or deleted. If you specify the created activity type for the label event, your workflow will run when a label is created but not when a label is edited or deleted.

    ```
    on:
      label:
        types:
          - created
    ```
  
  - If you specify multiple activity types, only one of those event activity types needs to occur to trigger your workflow. If multiple triggering event activity types for your workflow occur at the same time, multiple workflow runs will be triggered. For example, the following workflow triggers when an issue is opened or labeled. If an issue with two labels is opened, three workflow runs will start: one for the issue opened event and two for the two issue labeled events.

    ```
    on:
      issues:
        types:
          - opened
          - labeled
    ```


For more information about actions, see [Action](https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions#on).

Workflow triggers and events are key concepts in workflow automation and management systems. They help in defining the start, progression, and completion of various tasks within a workflow. Here's an overview:

### Workflow Triggers
Workflow triggers are specific conditions or actions that initiate a workflow. They determine when and how a workflow should start. Common types of triggers include:

1. **Time-Based Triggers**:
   - **Scheduled Time**: Initiates workflows at a specific time or interval (e.g., daily, weekly).
   - **Calendar Dates**: Triggers on specific dates or times (e.g., end of the month).

2. **Event-Based Triggers**:
   - **System Events**: Actions within a system such as a new file upload, a record update, or a new user registration.
   - **External Events**: Integrations with other systems or services, like receiving an email, API calls, or webhooks.

3. **Manual Triggers**:
   - **User-Initiated**: Manually started by a user through a button click or form submission.

4. **Conditional Triggers**:
   - **Condition-Based**: Triggered when specific conditions or rules are met (e.g., inventory level falls below a certain threshold).

### Workflow Events
Workflow events are occurrences within the workflow that may cause a change in the state or progress of the workflow. They can be internal to the workflow or external inputs that influence the workflow’s path. Common types of workflow events include:

1. **Task Completion**:
   - Events are triggered when a task is marked as complete, leading to the initiation of subsequent tasks.

2. **Status Changes**:
   - Events that occur when the status of an item changes (e.g., from "pending" to "approved").

3. **Conditional Events**:
   - Actions are taken when certain conditions within the workflow are met (e.g., approval is granted if a request is below a certain amount).

4. **Notification Events**:
   - Events that send notifications or alerts to users or systems (e.g., email notifications, SMS alerts).

5. **Error Events**:
   - Triggers when an error occurs in the workflow, often leading to error handling procedures or notifications.

6. **External Input Events**:
   - Events caused by external inputs, such as data received from an API or an external system interaction.

### Example Workflow Scenario
Consider a workflow for processing employee leave requests:

1. **Trigger**: An employee submits a leave request form.
2. **Event**: The system logs the submission and assigns the request to the manager for approval.
3. **Event**: The manager receives a notification to review the request.
4. **Event**: The manager approves or rejects the request.
   - **If approved**, an event triggers that updates the employee's leave balance and notifies HR.
   - **If rejected**, an event triggers that notifies the employee of the rejection.
5. **Event**: Upon approval, an event schedules the employee's leave on the company calendar.

### Implementing Workflow Triggers and Events
In modern workflow automation tools (like Zapier, Microsoft Power Automate, or Apache NiFi), these concepts are implemented through:

- **Triggers**: Defined by selecting an event or condition that starts the workflow.
- **Events/Actions**: Configured as steps within the workflow that define what happens after the trigger, including conditional logic, loops, and parallel processing.

### Best Practices
- **Clear Definitions**: Ensure that triggers and events are clearly defined and documented.
- **Error Handling**: Include error handling mechanisms to manage exceptions and failures.
- **Testing**: Regularly test workflows to ensure they trigger and respond to events as expected.
- **Scalability**: Design workflows to handle increased loads and multiple triggers/events efficiently.

By understanding and implementing workflow triggers and events effectively, organizations can automate repetitive tasks, enhance process efficiency, and improve overall productivity.
