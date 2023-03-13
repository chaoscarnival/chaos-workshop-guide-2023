# Chaos Workshop

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
- Add a new chaoshub by following the steps outlined here: https://developer.harness.io/docs/chaos-engineering/user-guides/add-chaos-hub. 
  
  Use the github   repo URL https://github.com/chaoscarnival/hub-workshop-2023
 
- Browse the newly added chaoshub. You will see 4 chaos experiments ready to be launched. 

  <img width="1718" alt="Screenshot 2023-03-13 at 4 29 50 PM" src="https://user-images.githubusercontent.com/21166217/224683043-41c3c8ff-c738-4fcb-bcb9-ca8407cd9f73.png">
  

## Online-Boutique: A Summary of the Chaos Experimentation Activity

- The workshop details chaos experiments against (an instrumented version of) the demo microservices application [Online Boutique](https://github.com/GoogleCloudPlatform/microservices-demo). The application is constantly under "usage" via a synthetic load generator. 
- The experiments involve injection of different types of chaos on a given microservice (ex: carts) OR multiple microservices accompanied by validation of specific constraints (hypotheses) around application behaviour and user impact. 
- The chaos experiment progress, its logs and eventually, the results can be viewed on the respective overview page, while real-time impact can be observed on the Grafana dashboard

*For more inputs on other experiment-related user actions on the chaos module, follow the live guided workshop during the Chaos Carnival (March 16 <CST>) / refer the video recording (to be updated once event concludes).*

## Launch Experiment #1 (State Chaos): `boutique-carts-pod-bounce`

#### UseCase

- In this experiment, we randomly bounce/delete pods belonging to the carts microservice. The intent of state chaos such as this is to verify impact upon pod kills that occur as a result of evictions, upgrades etc.,

- During this experiment, we validate the following hypotheses/constraints using "Resilience Probes": 

  - Healthy Kubernetes resource status prior to and after fault injection
  - Continuous availability of the microservice under test
  - Expected levels of latency on the website upon user actions (simulated via loadgenerator) 

#### Activity 

- Upon "Launch Experiment", select the appropriate chaos infrastructure (connected in the previous steps) & provide the appropriate `App Namespace` in the `Target Application` section. Proceed to run the chaos experiment.

#### Expected Result

- While the resource health is maintained before & after the experiment, the availability and performance constraints are not met, leading to probe failures and hence, a low resilience score. 

## Launch Experiment #2 (Network Chaos): `boutique-carts-degraded-network`

#### UseCase

- In this experiment, we inject network latency (with jitter, to randomize extent of latency) to the carts microservice to simulate a degraded cluster network. This is also one of the most popular ways to simulate latency between services across AZs/regions. The intent is to evaluate if the network delay is handled within the system OR is propagated upwards to cause degraded user experience on the website's transactions.  

- During this experiment, we validate the following hypotheses/constraints using "Resilience Probes": 

  - Healthy Kubernetes resource status prior to and after fault injection
  - Continuous availability of the microservice under test
  - Expected levels of latency on the website upon user actions (simulated via loadgenerator) 

#### Activity 

- Upon "Launch Experiment", select the appropriate chaos infrastructure (connected in the previous steps) & provide the appropriate `App Namespace` in the `Target Application` section. Proceed to run the chaos experiment.

#### Expected Result

- While the resource health is maintained before & after the experiment and the website continues to be available, the performance constraints are not met, leading to probe failure and hence, a low resilience score. 

## Launch Experiment #3 (Resource Chaos): `boutique-carts-cpu-starvation`

#### UseCase

- In this experiment, we hog the cpu resources in the pod belonging to the carts microservice, simulating a high-traffic situation in which the service is deprived of cpu cycles, leading to slower responses. The intent is to evaluate whether the slowness is handled within the system OR is propagated upwards to cause degraded user experience on the website's transactions. 

- During this experiment, we validate the following hypotheses/constraints using "Resilience Probes": 

  - Healthy Kubernetes resource status prior to and after fault injection
  - Continuous availability of the microservice under test
  - Expected levels of latency on the website upon user actions (simulated via loadgenerator)

#### Activity 

- Upon "Launch Experiment", select the appropriate chaos infrastructure (connected in the previous steps) & provide the appropriate `App Namespace` in the `Target Application` section. Proceed to run the chaos experiment.

#### Expected Result

- While the resource health is maintained before & after the experiment and the website continues to be available, the performance constraints are not met, leading to probe failure and hence, a low resilience score. 

## Launch Experiment #4 (Multi-Fault Chaos): `boutique-multi-fault-scenario`

#### UseCase

- In this experiment, we illustrate the ability to string faults together in a desired fashion to generate *complex scenarios* that reproduce past outage conditions OR are used as stressors/mechanisms to evaluate multi-component failure. 

#### Activity 

- Upon "Launch Experiment", select the appropriate chaos infrastructure (connected in the previous steps) & provide the appropriate `App Namespace` in the `Target Application` section of each individual faults. Proceed to run the chaos experiment.

#### Expected Result

- This experiment is oriented towards illustrating multi-fault capabilities. The probe successes/failures are aligned with the ones explained in the previous runs. 

## Share Your Workshop Results With The Harness Team

- Share Screenshots of the "Chaos Experiment Overview Page" for all 4 chaos experiments in this slack channel: https://join.slack.com/share/enQtNDkzNDc4MDkzMDUzMy1hM2I0MDEzMGM3MWJmYjBlMTE4ZjU4MDk1ZjQ2OWUyYTBmM2FlNzllNTUzNWY4N2E3MDRlZDc1OTMxNzMzMWI3 

**Note**: Please ensure that the screenshots cover the browser address bar with account info in the URL! 

