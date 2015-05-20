# Lab 4.2 TDD

----

### We can fix this! Feature branch

1. Confirm our tests work as things stand now ✔︎
1. Create a feature branch
1. Write a _failing_ test, then
  1. Write the correcting code
  1. Retest, if failure, try again, else
1. Commit and submit PR


----

### Create feature branch

```
git branch fix_homepage
git checkout fix_homepage
git status
```

----

### We can fix this!

1. Confirm our tests work as things stand now ✔︎
1. Create a feature branch ✔︎
1. Write a _failing_ test, then
  1. Write the correcting code
  1. Retest, if failure, try again, else
1. Commit and submit PR

----

### Write a _failing_ test

What is it we want to test?
- Either:
  - Contents of `/var/www/html/index.html`
  - Response from http://localhost:80

----

### Write test of index.html

Update `test/integration/core/serverspec/core_spec.rb`:

```ruby
describe file('/var/www/html/index.html') do
  it { should contain('Welcome to DevOpsDC')}
end
```

----

### Optional: Write test of http://localhost:80

Update `test/integration/core/serverspec/core_spec.rb`:

```ruby
describe command('curl -s http://localhost') do
  its(:stdout) { should_not contain('Ubuntu') }
  its(:stdout) { should contain('Welcome to DevOpsDC') }
end
```

----

### Test

1. Converge the _integration_ instance with `kitchen converge`
1. Verify with `kitchen verify`

----

### We can fix this!

1. Confirm our tests work as things stand now ✔︎
1. Create a feature branch ✔︎
1. Write a _failing_ test, then ✔︎
  1. Write the correcting code
  1. Retest, if failure, try again, else
1. Commit and submit PR

---

### Write the correcting code

----

### What _Chef_ resource will we manage?

<br>

----

### What _Chef_ resource will we manage?

`file`

----

### Update the core `recipe` for `file`

Update `recipe/core.rb` with

```ruby
file '/var/www/html/index.html' do
end
```


----

### Update the core `recipe` for `file`

Update `recipes/core.rb` with

```ruby
file '/var/www/html/index.html' do
  content "<h1>Welcome to DevOpsDC</h1>"
  owner   "www-data"
end
```
Then:
```
kitchen converge
kitchen verify
```

----

### We can fix this!

1. Confirm our tests work as things stand now ✔︎
1. Create a feature branch ✔︎
1. Write a _failing_ test, then ✔︎
  1. Write the correcting code ✔︎
  1. Retest, if failure, try again, else ✔︎
1. Commit and submit PR

----

### Commit and submit PR

```
git status
git add recipes test
git commit -m "Fixed homepage"
git push origin fix_homepage
```

----

### Submit Pull Request (PR)

- Navigate to https://github.com/cheffian/(fluxx)
- Submit PR (one of you)
- Approve PR (the other)

----







### Next: [Lab 4.2 TDD](lab_4.2-tdd.md)
