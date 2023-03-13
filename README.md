# Workshop

Welcome to the Chaos Workshop!! Follow the steps provided below to successfully complete the chaos workshop. Earn your certificate & win prizes by sharing the workshop completion details on #slack-channel !! 

## Prerequisites for the Chaos Workshop 

### Sign-Up on Harness SaaS Platform

- Sign-Up on the [Harness SaaS platform](https://app.harness.io) via email. 

- Click on the verification email received. 

- Choose the Chaos Engineering Module. This will enable a 14-day enterprise trial license.  

  <img width="1728" alt="choose-module" src="https://user-images.githubusercontent.com/21166217/224661235-f16ae004-f691-41f9-9c3d-fb7739e46f06.png">
  
  **Note**: Note the Account ID (underlined in red in the above screenshot). This will be needed while submitting request for the sandbox environment.
  
- You will see a modal asking to to "Enable Chaos Infrastructure To Run Your First Chaos Experiment". At this point, pause action on the Harness UI & proceed with the next step to obtain the sandbox environment.  

  <img width="1728" alt="enable-chaos-infra" src="https://user-images.githubusercontent.com/21166217/224663331-df557b3c-a952-471b-9609-a688d968177e.png">

### Obtain a Sandbox Environment to Run Chaos Experiments 

- Fill up and submit this [form](https://docs.google.com/forms/d/e/1FAIpQLScgLSi2W8LystCMSTP3SICSHfI8jADieU3Pbp-ZMvhhhSS0Fw/viewform) to request a timed (6 hours) sandbox environment to carry out the chaos workshop steps 

- In under 2 minutes, check your email and verify receipt of your sandbox config information, which consits of: 
  - A KubeConfig file, which you can download and use as the context for navigating the namespace provided 
    - **Note**: You will need `kubectl` setup in your local workspace to view the resources in your sandbox environment
  - URLs to a sample microservices application (which will be subjected to chaos during the workshop), the grafana dashboard where it is monitored along    with the corresponding prometheus endpoint.
  
## Setup The Chaos Infrastructure 

- Now, proceed with setting up of the chaos infrastructure. You will be needed to create a new "Environment", followed by the download of a manifest to install a "namespaced-scoped" chaos infra in the provided sandbox environment. 

https://developer.harness.io/docs/chaos-engineering/user-guides/connect-chaos-infrastructures

## Connect The Custom ChaosHub

## Launch Experiment #1 

### UseCase
### Things to Observe

## Launch Experiment #2

### UseCase
### Things to Observe

## Launch Experiment #3 

### UseCase
### Things to Observe

## Launch Experiment #4 

### UseCase
### Things to Observe

## Share Your Workshop Results With The Harness Team

