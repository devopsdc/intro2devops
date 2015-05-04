# intro2devops

## One Day Workshop on DevOps Essentials

Technical Goals:
- Introduce infrastructure automation as a concept with Chef as a model
- Introduce cloud infrastructure with chef-provisioning
- Introduce continuous delivery of apps/inf with Jenkins

Community Goals:
- Broaden the funnel of entering practitioners from under-represented backgrounds
- Introduce DevOps as
  - Cool
  - Valuable
  - Fun

See SETUP.md for technical preparation

## Outline

1. introductory.md
  - logistics
  - agenda
  - introductions
  - why devops
  - why diversity
  - technical goals
1. infrastructure.md
  - what is infrastructure?
    - automobile analogy
  - why automate it?
    - click-next dangers
    - repeatablity, speed
    - so let's get started, but first:
1. workstation_setup.md
  - connect to AWS workstation
  - set up local connection and Atom remote_file
1. chef_0.md
  - setting: we have to release our (non-dynamic) home page
    - we need to walk before we can run - so we'll start simple
  - how do config mgmt systems approach the problem?
    - Infrastructure as Code
      - Programmatically provision & configure components
      - Treat like any codebase
      - Reconstruct business from repository, data backup, and compute
    - Policy-based management
      - capture in code
      - Chef ensures nodes and compute resources comply
  - resources
  - test & repair
1. chef_1.md
  - enough lab with package, file, service and template to get hello world!
  - What's the DevOps story here?
1. code_collaboration.md
  - lab: bump versions and collaborate through GitHub PRs
  - lab: test your cookbook
  - lab: use Jenkins to ensure you're testing
  - optional_lab: use Jenkins to release your infrastructure
  - What's the DevOps story here?
1. operationalize.md
  - Why AWS
    - Biggest player
    - All other players borrow from them: Dig. Ocean, Google Cloud,
    - One I'm most familiar with
  - Why the cloud?
    - OpEx vs. CapEx
    - Elastic to demand
    - Instant provisioning
    - The Netflix story
1. aws_0.md
  - ec2
    - ami
    - instance size
    - security groups
      - the instances so far have been in the default security group, which only allows ingress from this set of IP addresses
      - can't reach it with your phone
      - the www machine needs to be world-accessible
  - load-balancing



## Attributions

* Jennifer Davis and Franklin Webber for TechSuperWomen materials
* Franklin Webber for https://github.com/learnchef/chefdk-fundamentals
