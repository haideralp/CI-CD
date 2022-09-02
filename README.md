# Continuous Integration And Continous Delivery/Deployment Pipeline

## Diagram Showing Overview of CI-CD Pipeline

![image](https://user-images.githubusercontent.com/97620055/188130100-d999e4e5-e0c3-4fc7-9863-ac209f7d0de2.png)

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

## Key Generation For Deployment

- Step 1: Generate a Public/Private key pair. 
    - Create key in your bash terminal using command > `ssh-keygen -t ed25519 -C haider.abedi@gmx.com`
    - Name the key that is identifiable.
    - Make sure your present in the `~/.ssh directory` and copy content in public key > `clip < ~/.ssh/jen122.pub`

- Step 2: Deploy Key on Github Repo
    - On the relevant Github repository, go to settings, click deploy and Add Deploy Key.
    - Ensure you allow for write acess and add key. Paste key and save.

## Configuring Webhooks

- Step 1: Under same repository settings, click on Webhoots and ADD webhook. 
    - Enter the Payload URL as your Jenkins IP followed by port 8080. > http://13.40.148.93:8080/git-webhook/
    - Content type - Select application / json.
    - For events to trigger, select to Send me everything. 

## Creating Jenkins Jobs 
    
    - Click New Item on the Jenkins Dashboard.
    - Enter Name of Project and Select Freestyle Project and click Ok.
    - Create 3 Jobs: CI, Merging and Deployment.
    
    ![CICD - jenkin job creation](https://user-images.githubusercontent.com/97620055/188126835-e0a589de-13cb-44c6-ba66-dacec52bbb60.PNG)
  
## First Job - Continuous Integration

- General Configs as below:

![firstjob-general](https://user-images.githubusercontent.com/97620055/188126992-a28a6315-bc0d-422f-ba1b-be25bb5861b8.PNG)

- Office 365 with Webhook on first job as that will get everything rolling after the triggering. 

![firstjob-webhook](https://user-images.githubusercontent.com/97620055/188127055-51ee6799-ba2a-40cf-b71f-b3f0b3859424.PNG)

- Configure the source management as follows:

![firstjob-source](https://user-images.githubusercontent.com/97620055/188129722-e6c2b35d-0ca3-42f5-921f-c1106acb106a.PNG)


- Tick the option for Triggering webhook from GitHub:

![firstjob-build trigger](https://user-images.githubusercontent.com/97620055/188129842-74e86aa6-4e4b-437b-b6ad-56801ecd4bf0.PNG)

- Next build the ennviroment for Jenkins as follows:

![firstjob-build environment](https://user-images.githubusercontent.com/97620055/188133935-8925db3f-dad8-4caa-b8a5-c6c3859dcadc.PNG)

- Under build option, select the option Execute Shell, enter your script here that will run:

![firstjob-build](https://user-images.githubusercontent.com/97620055/188138254-5e94469d-75fb-4237-a94f-467bf6beaab0.PNG)

- Once Job is stable and success, build onto the other job (stagins jobs in steps here)

![firstjob-post-build](https://user-images.githubusercontent.com/97620055/188148998-6d8c0834-1e37-4121-9f0b-d74ee4e3c4b9.PNG)


## Second Job -  Merging

- Create the merge job like that of first job however change the following settings:
   
   - Under source management do the following:
    
    ![secondjob-source](https://user-images.githubusercontent.com/97620055/188149419-702c4a39-ea58-455d-879c-ce5c3106d7ec.PNG)
   
   - Define post build actions as follows: 
    
    ![secondjob-postbuild](https://user-images.githubusercontent.com/97620055/188149506-e21b065f-090b-48a7-a062-8fceff1b5afc.PNG)


## Third Job - Delivery


## Fourth Job - Deployment



## Fifth Job - Configuring DB_HOST










#### Debugging Issues Common:

- Wrong AMI Ubunti 16.04LTS 1804 ami id
- AWS access denied
- port 22 timing out
- plugins available
- provisioning script incorrect

#### Key links / Tests Performed.

![https://docs.github.com/en/developers/webhooks-and-events/webhooks/creating-webhoo

# Dev Branch Commit Testing - Triggering Webook
# Merging Test
# Spartans we go war.
