# Lab 3


## Practice GitHub (GH) Workflow

A. _Fork_ your common GH repository for local dev
B. Correct documentation and submit _Pull Request_ (PR)
C. Collaborate to approve and _merge_ the change
D. Clean up


----

### Personalizing the lab

- Where `<fluxx>` appears, use your Fluxx group name.
  - For example: `ws.milk.cheffian.com` if 'milk' is your group
- Where (your password) appears, then supply the password
  - Your instructor should have provided this
- Where `<user>` appears, use either `alpha` or `bravo` per your team role.
- Where `<gh_user>`, substitute your personal GH account name


---

## A. _Fork_ your common GH repository for local dev

----

### Find your project repository (repo)

- Login to GitHub at
- Navigate to https://github.com/cheffian/<fluxx>
- Find the `Fork` button and _fork_ the repository
  - This creates your own copy/clone of the project

----

### Forking the repository

![lab3_forking](images/lab3_forking.png)

----

### Clone the repo for development

- Copy the `HTTPS clone URL`

![lab3_clone](images/lab3_clone.png)

----

- Then `clone` onto your _workstation_

```bash
cd  # change back to home directory
git clone https://github.com/intro2devops/<fluxx>.git
```

- And confirm you have the correct Git _remote_

```bash
cd <fluxx>
git remote -v
```
```
origin  https://github.com/intro2devops/fluxx.git (fetch)
origin  https://github.com/intro2devops/fluxx.git (push)
```

----

# Fini 3.A

We've demonstrated:
- Making a personal GitHub _fork_ of a code _repository_
- Making a _clone_ of our fork on the workstation

---

## B. Correct the documentation and submit a _pull request_

----

The `README.md` has an ugly typo, 'awsaume'. Let's fix it:

- _branch_ the repo to keep our work separate
- fix the typo in `nano` and save
- _commit_ the change with a _commit message_
- _push_ the change to our person GH repo
- submit a _pull request_ to the _upstream_ Cheffian repo

----

### Branch the repo

```
git branch fix_readme
git checkout fix_readme
```
```
Switched to branch 'fix_readme'
```

----
