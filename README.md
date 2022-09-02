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
## Creating Jenkins Jobs 
    - Click New Item on the Jenkins Dashboard.
    - Enter Name of Project and Select Freestyle Project and click Ok.
    - Create 3 Jobs: CI, Merging and Deployment.
  
## First Job - Continuous Integration



![https://docs.github.com/en/developers/webhooks-and-events/webhooks/creating-webhoo

# Dev Branch Commit Testing - Triggering Webook
# Merging Test
# Spartans we go war.
