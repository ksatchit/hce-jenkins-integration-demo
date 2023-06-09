# Notes for Demo Team 

Here are a list of things we considered before creating this demo block. FYI. 

#### 1. Make the Jenkins setup simple. We are looking at both existing Jenkins as well as new users here

- Ensure Jenkins bring-up as well as cleanup is swift. 
  - We have chosen Jenkins on Kubernetes 
- Don't add additional plugins and cause complexity as well as make Jenkins slower
  - Avoid Kubernetes, Kubernetes-CD, Kubernetes-CLI, GKE and other plugins. Pipeline syntax involves groovy classes, storing secret files etc., 
- Simplify application deployment & stability checks
  - Make Jenkins & Application co-located. Use custom images based on jenkins:lts & updated permissions to jenkins-admin svcaccount
  - Use rollout status to track health
  
#### 2. Simplify API calls to HCE

- Our [GraphQL APIs](https://apidocs.harness.io/chaos.html#mutation-runChaosExperiment) are extremely cumbersome for users to navigate. 
Despite being able to download curl commands from our [Postman collection](https://www.postman.com/harness-chaos-engineering/workspace/harness-chaos-engineering-public/request/25469526-b894f577-628d-416c-b360-00f2a00b1834), it is not easy to parameterize and push the command into a bash script due to the challenging task of escaping multiple special characters inside the original curl cmd.
- Instead, we have a simple CLI client to help construct the API calls and execute the commands. It can also output the fully formed curl cmd for need. 

#### 3. Use the same flow as the HCE CD-CE demo

- Deploy a microservice, subject it to a chaos experiment and rollback based on the chaos testing outcomes
- Parameterize requirements (experiment IDs) and expectations (resilience score) in the pipeline (just as the Harness step provides)

**Note**: Store account information and api keys as secrets
    
The detailed documentation for the tutorial/demo-block can be found in [tutorial.md](./tutorial.md) 






