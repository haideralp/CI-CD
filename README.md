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

    - Creat new job by selecting **New Item** on jenkin's dashboard.
    - Enter name of job and select **freestyle project** as the option and proceed by clicking OK.
    - Generate the following jobs:
    - 
        - Continous Integration 
        - Mergin (Dev to Main)
        - Continous Delivery (Manual Starting App)
        - Continour Deployment (Automating deployment of APP)

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
- Once changes have merged, I will prepare the EC2 instance as shown in (repository link), to expediate the process I will be using an **ami** that has the relevant dependeices intstalled.

- I have then configured the third job as follows for delivery so can test to see manually if app work in development environemnt.




- I have lannched app manually to see if it works. This can be shown as below:

![image](https://user-images.githubusercontent.com/97620055/188402716-7da57a10-1eb2-4141-86b1-aa12782c280e.png)

## Fourth Job - Deployment
- This job was used to take my delivery from app once verfied it works to automate the deployment without need for manual checks. 

- I configured the job as follows:


## Fifth Job - NodeApp to DB Connection

- In this job I will instruct jenkins to automate the creation of DB_HOST variable and connect to the node app as well as fetching data from seeds folder. 

- To do this I have run the following script as follows:




## Testing Automation of Deployment

- Once all these steps have been carried out, the following 3 pages will indicate the app has been successfully automated to deploy via jenkins.


    ### Page 1: App Working (Automated)
![app jenkin wokring page](https://user-images.githubusercontent.com/97620055/188400621-ecf26273-c1ad-4a23-8ab6-3140b69ddcd2.PNG)

    ### Page 2: Posts Working
![posts jenkin wokring page](https://user-images.githubusercontent.com/97620055/188400725-6c9c7dca-c4c0-4f90-8b26-d9f05487328b.PNG)

    ### Page 3: Fibonacci Generator Working
![fibonaaci jenkin wokring page](https://user-images.githubusercontent.com/97620055/188400805-b9a4ccc8-50e0-4222-b6b0-741509f2fe12.PNG)












#### Debugging Issues Common:

- Make sure read console ouput for each job - provisioning script issues.
- Using the wrong EC2 AMI (ensure Ubuntu 18.04 LTS)
- AWS access denied - ensure this is set up correctly and configured with right steps
- CANNOT GET POSTS - Specify Private IP4 address of DB in the variable.
- Port Timing Out Issues - (22) - Cross-reference the security groups rules for both APP and DB.
- Ensure correct plugins and dependencies are installed. 

#### Key links:

![https://docs.github.com/en/developers/webhooks-and-events/webhooks/creating-webhook


