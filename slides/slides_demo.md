# Lab 0

### Establish Remote Working Environment

A. Use an SSH client to securely connect to remote workstation<br>
B. ~~~Use Atom and the `remote-sync` plugin to edit code on your local laptop~~~<br>
C. Verify software on your remote workstation

Note: So when we navigate to https://github.com/devopsdc/intro2devops/blob/master/slides/slides_demo.md we see a mild-mannered markdown lab walkthru

----

### Context

We're using a remote workstation with all packages and connectitivy
preconfigured. This eliminates a lot of installation and troubleshooting on
student laptops. However, the remote Linux workstations may not have editors
that are comfortable for you to use, so we'll use Atom, a free editor, with a
remote-sync plugin.

Note: But when we supercharge our system with https://github.com/webpro/reveal-md we reveal a powerful hidden identity.

----

<!-- .slide: data-background="#000000" -->

## A: Remote connection

Note: `reveal-md slides_demo.md` and/or in the looper dir: `reveal-md`

----

<!-- .slide: data-background="#ffffff" -->

### A.1: Mac Os X

Use the `Terminal` application to make an ssh connection your workstation:

- Open the `Terminal` app from /Applications/Utilities
- At the command prompt type: `ssh alpha@ws.<fluxx>.devopsdc.com`
  - At the prompt "Are you sure you want to continue connecting?" answer: "yes"
  - For the password, enter: password (it won't be displayed)
 - The login sequence should look like this:

----


Areas of user input shown in red:

![Alt text](images/putty.png)

----

- You should get a prompt something like, `alpha@ip-10-230-43-114:~$ `
 - Type `whoami`
 - If the result is `alpha`, continue to Section B

```bash
alpha@ip-10-230-43-114:~$ whoami
alpha
```

----


<!-- .slide: data-background="http://static.guim.co.uk/sys-images/Arts/Arts_/Pictures/2015/2/18/1424262922461/Exodus-II-Dubai-UAE-2010--001.jpg" -->

## Infrastructure


----


# Some other things

* v2 of the aws-sdk no longer requires `nokogiri`
  * https://github.com/aws/aws-sdk-ruby/pull/745
* so Route53 doesn't either --
* Run chef-client

----

# Also:

- PRs to real repos:
  - https://github.com/cheffian/sun/pulls?q=is%3Apr+is%3Aclosed
  - https://github.com/cheffian?tab=repositories
- Easter eggs --
```
sl
```

---


# A table

| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |

----

# A table

| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| * list      | right-aligned | $1600 |
| * list      | ![Alt text](images/AWS_market_share.png)    |   $12 |
| zebra stripes | are neat      |    $1 |

---

![Alt text](images/AWS_market_share.png)


----

<!-- .slide: class="two-floating-elements" -->
## Title

* List item 1
* List item 2
* List item 3

![Alt text](images/AWS_market_share.png)

----

<!-- .slide: class="two-floating-elements" -->
## Title

* List item 1 adlja d alsdfn asidlfn adfs lkjasdf las dflkjas dflaksfdalksj asdlfj
* List item 2
* List item 3
* List item 1
* List item 2
* List item 3
* List item 1
* List item 2
* List item 3
* List item 1
* List item 2
* List item 3

<img src="images/AWS_market_share.png" alt="Drawing" style="width: 400px;"/>

----

# Ruby

```
def foo
  print "bar\n"
end
```


----

# Bash

```bash
for i in foo bar baz; do
  mkdir $i
done
```

----

 - You should get a prompt something like, `alpha@ip-10-230-43-114:~$ `
   - Type `whoami`
   - If the result is `alpha`, continue to Section B


### A.2: Windows 7 or 8

Install `Putty` and Copy to your Desktop:

- In your browser, go to http://www.putty.org
- Click through on the "You can download PuTTY here." link
- Click on the `putty.exe` link
  - Accept the download and 'Save' Putty.exe
  - Click 'View Downloads'
  - Right click on 'putty.exe', select 'Open containing folder'
  - From the Downloads folder, drag 'putty.exe' to your desktop


Use `Putty` to make an ssh connection your workstation:

- Double-click the `putty.exe` from the step above
- In the connection dialog window, fill in:
  - Host Name: `ws.<fluxx>.devopsdc.com`
  - In the 'Saved Session' box, enter a name, `ws`
  - Then click `Save`
  - Then click `Open`
- You'll get a "PuTTY Security Alert" about the host key not being cached.
  Select `Yes`
- In the terminal window:
  - Login as: `alpha`
  - Password for `alpha@ws.<fluxx>.devopsdc.com` is `your password`

- You should get a prompt something like, `alpha@ip-10-230-43-114:~$ `
  - Type `whoami`
  - If the result is `alpha`, continue to Section B

## B: Remote editing with Atom
