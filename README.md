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
 
 