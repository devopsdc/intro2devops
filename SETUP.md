## Todo:
- Work with subdomain DNS in AWS
  - Create a new hosted zone, e.g. `fluxx.cheffian.com` in Route53
  - Note the NS records assigned to your new zone
  - In the parent zone, `cheffian.com`, add an NS record for `fluxx.cheffian.com` zone with the servers noted in the step above
- Get an AWS account - ASK at DevOpsDC planning
- Get Excella networking information
- Get lunch and breaks


## Local Workstation

- Atom with remote editing
- Putty or ConEmu or iTerm or Terminal

## Remote Resources

Each pair gets:
- combined Jenkins/ChefServer at jenkins.fluxx.cheffian.com/chefserver.fluxx.cheffian.com
- their own workstation at a.fluxx.cheffian.com and b.fluxx.cheffian.com
- a pre-provisioned dev.fluxx.cheffian.com

Fluxx domains (longer names at end)
- Party
- Milk
- Eye
- Sun
- Brain
- Moon
- Dreams
- Time
- Sleep
- Music
- Money
- Rocket
- Bread
- Love
- Peace
- Toaster
- Cookies
- Television
- Chocolate

Remote workstations have either IAM roles or the AWS keys to
- provision ELB, prod nodes, autoscale group

## Supplies

https://www.stickermule.com/user/1070644219/stickers

## Slides

https://github.com/webpro/reveal-md
