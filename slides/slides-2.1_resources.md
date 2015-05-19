# Resources

![slides_splash_resources](images/slides_splash_resources.png)

----

# About Resources

A resource is a statement of configuration policy that:

* Describes the desired state for a configuration item
* Declares the steps needed to bring that item to the desired state
* Specifies a resource type---such as ``package``, ``template``, or ``service``
* Lists additional details (also known as attributes), as necessary
* Are grouped into recipes, which describe working configurations

----

# Objectives

* Understand resource types

----

# Resources Types

Use |chef| resources to manage a piece of the system:

* package
* template
* service
* file
* user
* machines
* registry key
* aws security groups
* aws VPCs

and more!

----

# Resource Type - package

A package to be installed:

```ruby
package "haproxy" do
  action :install
end
```

----

# Resource Type - file

A file that should be generated:

```ruby
file "/etc/motd" do
  content "Property of Chef Software, Inc."
end
```

----

#   Resource Type - service

A service that should be started:


```ruby
service "haproxy" do
  supports :restart => :true
  action [:enable, :start]
end
```

----

# Resource Type - aws_security_group

A security group to control network access in AWS

```ruby
with_driver 'aws::us-east-1' do
  aws_security_group 'ws.fluxx' do
    description     'ws.fluxx'
    inbound_rules   '71.178.0.0/16' => 22
  end
end
```

----

# Resource Type - virtual machine

A machine to be provisioned

```ruby
with_driver 'aws::us-east-1' do
  machine 'ws.fluxx' do
    action :allocate

    add_machine_options bootstrap_options: {
      instance_type: 'm1.small',
      security_groups: [ 'ws.fluxx' ]
    }
  end
end
```

---


# Resources - Syntax

A resource is a statement of configuration policy that:

* Describes the desired state for a configuration item
* Declares the steps needed to bring that item to the desired state
* Specifies a resource type---such as ``package``, ``template``, or ``service``
* Lists additional details (also known as attributes), as necessary
* Are grouped into recipes, which describe working configuraitons

----

# Objectives

* Understand the resource syntax
* Understand how to declare resources in recipes

----

# Syntax - Resource Type

A resource has a type:

```ruby
file
```

----

# Syntax - Resource Name

A resource has a name:

```ruby
file "hello.txt"
```

----

# Syntax - Resource Keywords


A resource includes details between keywords ``do`` and ``end``:

```ruby
file "hello.txt" do
   ...
end
```

----

# Syntax - Resource Action

A resource describes the state of something by declaring an action:

```ruby
 file "hello.txt" do
   action :create
 end
```

----

# Syntax - Resource Syntax In Plain English


The file named ``hello.txt`` should be created:

```ruby
 file "hello.txt" do
   action :create
 end
```

----

# Syntax - Resource Attributes


A resource includes additional details---attributes:

```ruby
file "hello.txt" do
 action :create
 content "Hello, world!"
 mode "0644"
 owner "chef"
 group "chef"
end
```

----

# Syntax - Resource - In English


The TYPE named NAME should be ACTION’d with ATTRIBUTES:

```ruby
file "hello.txt" do
 action :create
 content "Hello, world!"
 mode "0644"
 owner "chef"
 group "chef"
end
```

----

# Recap

* Understand the resource syntax
* Understand how to declare resources in recipes

---

# Resource - Test and Repair

![slides_splash_resources](images/slides_splash_resources.png)

----

# About Resources

A resource is a statement of configuration policy that:

* Describes the desired state for a configuration item
* Declares the steps needed to bring that item to the desired state
* Specifies a resource type---such as ``package``, ``template``, or ``service``
* Lists additional details (also known as attributes), as necessary
* Are grouped into recipes, which describe working configurations

----

#  Objectives

* Understand how resources test and repair the system

----

# Test and Repair

Resources follow a test and repair model:

* Is a resource currently in the desired state? (test)
* If YES, do nothing
* If NO, then bring the resource into the desired state (repair)

----

<!-- .slide: data-background="images/test_and_repair_model_template_01.png" -->

<br>

----

<!-- .slide: data-background="images/test_and_repair_model_template_02.png" -->

<br>

----

<!-- .slide: data-background="images/test_and_repair_model_template_03.png" -->

<br>

----

<!-- .slide: data-background="images/test_and_repair_model_template_04.png" -->

<br>

----

<!-- .slide: data-background="images/test_and_repair_model_template_05.png" -->

<br>

----

<!-- .slide: data-background="images/test_and_repair_model_template_06.png" -->

<br>

----

<!-- .slide: data-background="images/test_and_repair_model_template_07.png" -->


<br>

----

# Recap

* Understand how resources test and repair the system

----

# Next

* [Lab 1: Resources](lab-1_resources.md)
