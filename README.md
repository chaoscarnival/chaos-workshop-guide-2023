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

- Now, proceed with setting up of the chaos infrastructure on the "default project". You can create a dedicated/new project if you wish. 
- You will be needed to create a new "Environment", download the installation manifest for the  chaos infra and apply it the provided sandbox environment. The detailed set of steps to achieve this can be found here: https://developer.harness.io/docs/chaos-engineering/user-guides/connect-chaos-infrastructures

**Note**: Please select the "Namespace Mode" option for chaos infrastructure. Selection of "Cluster Wide" option can result in failure/is unsupported for this workshop. 

## Connect The Custom ChaosHub

- The project is already configured with the "Enterprise ChaosHub" which consists of all the supported faults. However, to simplify things, we have a
  dedicated/custom chaos artifact source for this workshop. 
- Add a new chaoshub by following the steps outlined here: https://developer.harness.io/docs/chaos-engineering/user-guides/add-chaos-hub. Use the github   repo URL https://github.com/chaoscarnival/hub-workshop-2023
- Browse the newly added chaoshub. You will see 4 chaos experiments ready to be launched. 

  <img width="1718" alt="Screenshot 2023-03-13 at 4 29 50 PM" src="https://user-images.githubusercontent.com/21166217/224683043-41c3c8ff-c738-4fcb-bcb9-ca8407cd9f73.png">
  

## Online-Boutique: A Summary of the Chaos Experimentation Activity

- The workshop details chaos experiments against (an instrumented version of) the demo microservices application [Online Boutique](https://github.com/GoogleCloudPlatform/microservices-demo)  
- The experiments involve injection of different types of chaos on a given microservice (ex: carts) OR multiple microservices accompanied by validation of specific constraints (hypotheses) around application behaviour and user impact. 
- The chaos experiment progress, its logs and eventually, the results can be viewed on the respective overview page, while real-time impact can be observed on the Grafana dashboard

For more inputs on other experiment-related user actions on the chaos module, follow the live guided workshop during the Chaos Carnival (March 16 <CST>) / refer the video recording {to be updated once event concludes}. 

## Launch Experiment #1 (State Chaos): `boutique-carts-pod-bounce`

### UseCase

In this experiment, we randomly bounce/delete pods belonging to the carts microservice  

### Things to Observe

## Launch Experiment #2 (Network Chaos)

### UseCase
### Things to Observe

## Launch Experiment #3 (Resource Chaos)

### UseCase
### Things to Observe

## Launch Experiment #4 (Multi-Fault Chaos)

### UseCase
### Things to Observe

## Share Your Workshop Results With The Harness Team

