## Supplies

- https://www.stickermule.com/user/1070644219/stickers
- Fluxx cards
- Verizon Puck
- iPad and charger and cable
- Macbook and charger
- Mouse and keyboard


## Todo:

- See issues for this repo
- The external IP address 50.241.130.54. 

## Local Workstation

- Atom with remote editing
- Putty or ConEmu or iTerm or Terminal

## Chef Server

- Using `chefserver.cheffian.com`
- Creating users alpha, bravo and jenkins:
```
      for user in alpha bravo jenkins; do
        sudo chef-server-ctl user-create $user $user cheffian pburkholder+$user@chef.io $secret -f $user.pem
      done
```
- Then add to new org, `fluxx`
```
      org=fluxx
      sudo chef-server-ctl org-create $org $org -f $org.pem -a pdb -a alpha -a bravo -a jenkins
```
- Add all the users as admins of fluxx (except jenkins):
```
      for user in pdb alpha bravo; do
        chef-server-ctl org-user-add $org -a $user
      done
```
- Copy all the pems to $HOME/.chef/cheffian
  - $HOME/.chef/knife.rb can use 'pdb' as the node name and 'pdb.pem' as the client key
  - $HOME/.chef/knife.rb chef_server_url is currently "https://chefserver.cheffian.com/organizations/fluxx" but will need to use an ENV var for multi-org
- Berksfiles are unhappy about the SSL certs, so
  - `knife ssl fetch https://chefserver.cheffian.com` to create `~/.chef/trusted_certs/chefserver.cheffian.com.pem`
  - Then append all the others with: `cat /opt/chefdk/embedded/ssl/certs/cacert.pem >> ~/.chef/trusted_certs/chefserver_cheffian_com.crt`
  - And either set the evn var, or put this as the first line of Berksfile:
      ```
      ENV['SSL_CERT_FILE'] = "#{ENV['HOME']}/.chef/trusted_certs/chefserver_cheffian_com.crt"
      ```
- Set up user-data in i2d_aws/libraries/helpers.rb to use new server and orgs
- Set up chef-repo/.chef/fluxx.rb to use the fluxx org
- For the client to work, the self-signed cert needs to go on the client box, so user-data helper now does that, and `client.rb` on box has:
       ```
       ssl_ca_file      '/etc/chef/chefserver_cheffian_com.crt'
       ```


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

## AWS notes

### WS example

- launch configuration uses: `iam_instance_profile: 'pburkholder-ec2-bootstrap'`
```
aws iam get-instance-profile --instance-profile-name 'pburkholder-ec2-bootstrap'
# shows role name is pburkholder-ec2-bootstrap
aws iam list-attached-role-policies --role-name 'pburkholder-ec2-bootstrap'
# show role policies are get-object-s3-pburkholder-ec2-bootstrap
#   and change-chefdemo-net-route53-records-pburkholder'
aws iam get-policy --policy-arn arn:aws:iam::862552916454:policy/get-object-s3-pburkholder-ec2-bootstrap
aws iam get-policy-version --policy-arn arn:aws:iam::862552916454:policy/change-chefdemo-net-route53-records-pburkholder --version-id v2
```
- have those 2 policies for managing Route53 and getting s3 objects
- have s3 bucket for user-data bootstrap
  - pburkholder-ec2-bootstrap
    - singleton
    - group

- chefdemo.net is zone Z20GXCA1KGHB6A
- created policy:  change-chefdemo-net-route53-records-pburkholder
  - Based on http://docs.aws.amazon.com/Route53/latest/DeveloperGuide/UsingWithIAM.html
- created role:  manage-chefdemo-route53-pburkholder
- created 'instance profile' "If you use the AWS Management Console to create a role, the console automatically creates an instance profile and gives it the same name as the role"
- Add instance profile to launch configuration


## Slides

Slides are written in Markdown and displayed with `reveal-md` from https://github.com/webpro/reveal-md

Install per the README, then `reveal-md slides/`

Added chef_slides style, and this to the `chef_slides.css` file under /usr/local/lib/node-modules/reveal-md....

```
.two-floating-elements > ul ~ p,
.two-floating-elements > p ~ ul {
  max-width: 50%;
  float: left;
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box; }
.two-floating-elements > p ~ ul {
  margin-left: 0; }
```

per the answer at https://github.com/hakimel/reveal.js/issues/841
