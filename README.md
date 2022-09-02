# Continuous Integration And Continous Delivery/Deployment Pipeline

## Diagram Showing Overview of CI-CD Pipeline

![image](https://user-images.githubusercontent.com/97620055/187897272-42bf8b40-13ab-451b-9e12-28a439e8c8d1.png)


## Key Elements of CI/CD Pipeline:

- Continous Integration (CI) -  developers making small changes and checks to their code. This process is automated to ensure that teams can build, test, and package their applications in a reliable and repeatable way. 

- Continuous Delivery (CD) - automated delivery of completed code to environments like testing and development. CD provides an automated and consistent way for code to be delivered to these environments.


- Continous Deployment (CD/CDE) -  next step of continuous delivery. Every change that passes the automated tests is automatically placed in production, resulting in many production deployments.


- Github - online code repository tool used as part of CI.  Provides hosting platform for version control and collaboration.


- Webhooks - listen to changes from developers and delivers messages to other services, for example Jenkins.

- Jenkins -  open source automation server, allows to reliably build, test, and deploy their software.

- Master Node > main server in jenkins involved in execution to Cloud after tests are passed in agents node or feedback to local host for potential issues. 

- Agent / Slave Node > Provide desiredtesting environment (javascript executables) as determined from master node.

## Benefits of CI-CD Pipeline

- Automated testing enables continuous delivery, which ensures software quality and security and increases the profitability of code in production.
- CI/CD pipelines enable a much shorter time to market for new product features, creating happier customers and lowering strain on development.
- The great increase in overall speed of delivery enabled by CI/CD pipelines improves an organization’s competitive edge.
- Automation frees team members to focus on what they do best, yielding the best end products.
- Organizations with a successful CI/CD pipeline can attract great talent. By moving away from traditional waterfall methods, engineers and developers are no longer bogged down with repetitive activities that are often highly dependent on the completion of other tasks. 

# Creating CI-CD Pipeline

## Key Generation & Deployment

- Step 1: Generate a Public/Private key pair. 
    - Create key in your bash terminal using command >
    - Name the key that is identifiable.
    - Make sure your present in the ~/.ssh directory and copy public key.
- Step 2: Deploy Key on Github Repo
    - On the relevant Github repository, go to settings, click deploy and Add Delploy Key.
    - Ensure you allow for write acess and add key. Paste key and save.
## Configuring Webhooks
    - Step 1: Under same repository settings, click on Webhoots and ADD webhook. 
    - Enter the Payload URL as your Jenkins IP followed by port 8080. >
    - Content type - Select application / json.
    - For events to trigger, select to Send me everything. 
y
## Creating Jenkins Jobs 
    - Click New Item on 
Step 3: Creating Jenkins Jobs
On the Jenkins Dashboard, click on New Item
Enter a the name in convetion for the job
Select Freestyle project
Click Ok
Create a job for CI, merging and deployment
Step 4: Continuous Integration (CI) Job
General
Click Discard old builds and keep the max number of build to 2
Click GitHub project and add the HTTP URL of the repository
Office 365 Connector
Click Restrict where this project can be run, then set it as sparta-ubuntu-node
Source Code Management
Select Git
In Repositories:
Repository URL: insert the SSH URL from GitHub
Credentials:
Next to Credentials, click Add > Jenkins
Select Kind as SSH Username with private key
Set a suitable description and enter the private key directly. The private key is in your ~/.ssh directory. Ensure that the begin and end text of the key is included.
With the credential added, select the one you created
Branches to build: set to */dev (dev branch)
Build Triggers
Click GitHub hook trigger for GITScm polling
Build Environment
Click Provide Node & npm bin/ folder to PATH
Build
Click Add build step > Execute Shell
In command, enter the following code:
cd app
npm install
npm test
Post-build Actions
Select Add post-build action > Build other projects
Insert the project name for the merge job
Ensure Trigger only if build is stable is selected
Step 5: Merge Job
General
Click Discard old builds and keep the max number of build to 2
Click GitHub project and add the HTTP URL of the repository
Office 365 Connector
Click Restrict where this project can be run, then set it as sparta-ubuntu-node
Source Code Management
Select Git
In Repositories:
Repository URL: insert the SSH URL
Credentials: select the credential you created earlier
Branches to build: set to */dev (dev branch)
Build Environment
Select Provide Node & npm bin/ folder to PATH
Post-build Actions
First, select Add post-build action > Git Publisher
Click Push Only If Build Succeeds
In Branches:
Branch to push: main
Target remote name: origin
Next, select Add post-build action > Build other projects
Insert the project name for the deploy job
Ensure Trigger only if build is stable is selected
Ensure the Build other projects block is below the Git Publisher block
![https://docs.github.com/en/developers/webhooks-and-events/webhooks/creating-webhoo

# Dev Branch Commit Testing - Triggering Webook
# Merging Test
# Spartans we go war.
