# Lab 2

### Practice Resource Test/Repair

A. Practice Test&Repair with `chef-apply`<br>
B. Write a small `chef-apply` recipe

----

## Your domain and password

- Where `<fluxx>` appears, use your Fluxx group name.
  - For example: `ws.milk.devopsdc.com` if 'milk' is your group
- Where (your password) appears, then supply the password
  - Your instructor should have provided this
- Where `<user>` appears, use either `alpha` or `bravo` per your team role.

----

## Tip

### Don't forget the Up arrow
### When repeating commands

---

## A: Add new resources with `chef-apply`

- First, use `ssh` or `putty` to connect as:

```bash
<user>@ws.<fluxx>.devopsdc.com
```

----

### Try it out:

- Predict what the following command will do,
  - then type it and press `Enter`

```bash
chef-apply -e 'package "fortune-mod" do; action(:install); end'
```

----

### Oops...

```
E: Unable to lock the administration directory
   (/var/lib/dpkg/), are you root?
```

- That failed because only 'root' can install packages
  - `chef-apply`, and `chef-client` need 'root', or `sudo`
  - try this:

```bash
sudo chef-apply -e 'package "fortune-mod" do; action(:install); end'
```

----

### Now what?

```bash
fortune
All things that are, are with more spirit chased than enjoyed.
		-- Shakespeare, "Merchant of Venice"
```
```
fortune
Try to value useful qualities in one who loves you.
```

----

### Again, again...

- Predict what the following command will do,
  - then run it.

```bash
sudo chef-apply -e 'package "fortune-mod" do; action(:install); end'
```

----

### And remove

- Predict what the following commands will do,
  - then run them.

```bash
sudo chef-apply -e 'package "fortune-mod" do; action(:remove); end'
```
```
fortune
```

----

### Changes outside of C.M.

- Systems can drift,

```
sudo apt-get remove fortune-mod
```
```
fortune  # How sad, no fortunes!
```


----

### Changes outside of C.M.

- Systems can drift,
  - Configuration management brings them back
```
sudo chef-apply -e 'package "fortune-mod" do; action(:remove); end'
```
```
fortune
Celebrate Hannibal Day this year.  Take an elephant to lunch.
```

---

## B. Write a `chef-apply` recipe

----

### Let's edit

```
nano easter_eggs.rb
```

----

#### Save easter_eggs.rb

```ruby
easter_eggs = %w(fortune-mod cowsay sl)

easter_eggs.each do |egg|
  print "Egg: ", egg, "\n"
end
```

----

- What do you expect from this command?
```
ruby easter_eggs.rb
```

----

- Change `easter-eggs.rb` to

```ruby
easter_eggs = %w(fortune-mod cowsay sl)

easter_eggs.each do |egg|
  package egg do
    action :install
  end
end
```

----

- Now, what will happen when you run?
```
sudo chef-apply easter_eggs.rb
```

----

### Just for fun

- try the following commands:
```
fortune | cowsay
```
```
fortune | cowsay -f tux
```
- What happens when you finger-fumble `ls`?
```
sl
```
