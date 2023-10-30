
![TFE_TFC Branching](https://github.com/losojos27/terraform-gitops-flow/assets/5779465/b3a31eb7-5efb-442f-b92f-6d6e165e0778)

external link: [https://lucid.app/lucidchart/c86100f5-71c8-4010-aa08-f2bcfb6738c3/edit?viewport_loc=77%2C-1305%2C2387%2C1768%2C0_0&invitationId=inv_cb771d32-1364-49b4-983c-7e8a07f95cac](url)

## What is GitOps?

GitOps is an operational framework that takes DevOps best practices used for application development such as version control, collaboration, compliance, and CI/CD, and applies them to infrastructure automation.

## Why adopt GitOps?

Advantages of adopting a GitOps (like) workflow to manage your infrastructure.

- Improved collaboration and version control: GitOps allows for easy collaboration among team members as everyone can contribute to the infrastructure code using Git's branching and merging capabilities. This ensures that changes are versioned and easily trackable, reducing errors and conflicts.
- Reliable and reproducible infrastructure deployments: By using Git as the single source of truth for the infrastructure code, it becomes easier to roll back to a previous known good state in case of issues or failures. This promotes reproducibility and reliability in infrastructure deployments.
- Enhanced auditability and compliance: With GitOps, all changes to the infrastructure code are logged and can be easily audited. This helps in complying with security and regulatory requirements by providing a clear history of who made what changes and when.
- Automated and streamlined deployments: GitOps encourages the use of automation tools and processes for infrastructure deployments. This helps in reducing manual errors and ensures that deployments are consistent and repeatable across environments.
- Infrastructure as Code (IaC) best practices: GitOps aligns with the principles of Infrastructure as Code, allowing engineers to manage infrastructure just like any other software development project. This brings the benefits of code review, continuous integration, and automated testing to the management of infrastructure.
- Easy rollback and disaster recovery: In case of a failed deployment or a disaster, GitOps enables easy rollback to a known good state by rolling back to a previous commit. This minimizes downtime and allows for quick recovery.
- Scalability and extensibility: By using a GitOps workflow, it becomes easier to scale and extend infrastructure configurations. As the infrastructure code is already versioned and managed in Git, making changes, adding new features, or introducing new environments becomes simpler and less error-prone.
- Continuous Integration and Continuous Delivery (CI/CD) integration: GitOps can be seamlessly integrated with CI/CD pipelines, allowing for automated testing, build, and deployment workflows. This enables faster and more frequent releases while maintaining the stability and reliability of the infrastructure.
- DevOps culture promotion: Adopting GitOps encourages collaboration, communication, and transparency among developers, operations, and other stakeholders. It aligns with the principles of DevOps, promoting a culture of shared responsibility and continuous improvement.

## How to Manage Git Branches and Pull Requests in a DevOps Environment using GitOps

This guide will walk you through the process of managing Git branches and pull requests in a typical DevOps environment. 

### Branches

We will cover the three main branches - Prod, Stage, and Dev - and explain their deployment environments and pull request requirements. Additionally, we will outline the necessary approvals needed before merging pull requests. 

1. Prod Branch:
- This branch represents the production environment.
- New branches cannot be created from the prod branch.
- It only accepts pull requests from the stage branch; no other branch is allowed.
- Pull requests from the stage branch must be reviewed and approved by the product owner.

2. Stage Branch:
- This branch represents the staging environment.
- Only accepts pull requests from the dev branch; pull requests from other branches are not allowed.
- Can make a pull request only to the prod branch.
- Pull requests from the dev branch must be reviewed and approved by the technical lead.

3. Dev Branch:
- This branch represents the development environment.
- Only accepts pull requests from feature/bugfix branches; pull requests from user branches are not allowed.
- Can make a pull request only to the stage branch.
- Serves as the base branch for feature or bugfix branches.

### Now let's go through the steps to effectively manage these branches and their pull requests.

Step 1: Clone the Repository
- Start by cloning the repository to your local machine using the following command:
```
git clone <repository_url>
```

Step 2: Create a New Branch
- Before starting any development work, create a new branch from the dev branch using a descriptive name for your feature/bugfix. For example:
```
git checkout -b feature/my-new-feature dev
```

Step 3: Develop and Commit Your Changes
- Make the necessary changes to your code and commit them locally as you progress:
```
git add .
git commit -m "Implement my new feature"
```

Step 4: Push Your Branch
- Once you are satisfied with your changes, push your branch to the remote repository:
```
git push origin feature/my-new-feature
```

Step 5: Create a Pull Request
- Go to the repository's web interface and navigate to the pull request section.
- Click on "New pull request" and select your branch (feature/my-new-feature) as the source branch and the dev branch as the target branch.
- Write a clear and concise description of your changes and click on "Create pull request" to submit it.

Step 6: Review and Approval Process
- The technical lead will receive a notification about the pull request and review the changes made.
- If approved, the technical lead will merge your pull request into the dev branch.

Step 7: Pull Request from Dev to Stage
- Once your changes are merged into dev, you can create a pull request to merge dev into the stage branch.
- Follow the same steps as mentioned in Step 5, but this time select dev as the source branch and stage as the target branch.
- The technical lead will review and approve this pull request as well.

Step 8: Pull Request from Stage to Prod
- Similarly, after your changes have been merged into the stage branch, you can create a pull request to merge stage into prod.
- Follow the same steps as mentioned in Step 5, but this time select stage as the source branch and prod as the target branch.
- The product owner will review and approve this pull request.

Keep in mind that these steps should be followed for each new feature or bugfix branch that you create.

By following this branch and pull request workflow, you can ensure proper code reviews and approvals before deploying changes to different environments in your DevOps pipeline.
