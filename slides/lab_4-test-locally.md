# Lab 4

## Test Locally

----

A. View http://dev.<fluxx>.devopsdc.com <br>
&nbsp; &nbsp; It should be relevant, lets fix<br>
B. Confirm current test suite<br>
C. Update the tests, then code to pass the test<br>
D. Commit and submit PR<br>


Note: It's the repo that configures your workstation, your dev node, your ci node and all the other bits for running this workshop.  We'll use this cookbook to make www.devopsdc.com real.

----

### View from Chrome

http://dev.<fluxx>.devopsdc.com
![lab4_dev_page_chrome](images/lab4_dev_page_chrome.png)

----

### View from 'elinks'

```
elinks http://dev.<fluxx>.devopsdc.com
```
![lab4_dev_page_elinks](images/lab4_dev_page_elinks.png)

----

### We can fix this! W/ testing

1. Confirm our tests work as things stand now
1. Create a feature branch
1. Write a _failing_ test, then
  1. Write the correcting code
  1. Retest, if failure, try again, else
1. Commit and submit PR

---

# Fixing DevOpsDC

----

### Let's look at the code in charge

```
cd ~/<fluxx>/cookbooks/i2d_web
tree .
```
```
$ tree .
.
├── Berksfile
├── chefignore
├── metadata.rb
├── README.md
├── recipes
│   ├── core.rb
│   └── default.rb
├── run_tests.sh
├── spec
│   ├── spec_helper.rb
│   └── unit
│       └── recipes
│           └── core_spec.rb
└── test
    └── integration
        ├── core
        │   └── serverspec
        │       └── core_spec.rb
        └── helpers
            └── serverspec
                └── spec_helper.rb
```

----

### What with these tests?

```bash
# more run_tests.sh
foodcritic -f any .
rspec
kitchen test
```

----

### FoodCritic - Lint

* A `lint` tool for Chef
* Checks for common problems
  * zero-configuration (almost)
* http://foodcritic.io

----

### Rspec - Unit

* `ChefSpec` extends the `rspec` language
* Tests `chef` resources in memory
  * See tests under `spec/` directory
* https://github.com/sethvargo/chefspec

----

### Test Kitchen - Integration

* Runs Chef inside a virtual machine
* Tests state with ServerSpec
  * See tests under `tests/integration`
* https://serverspec.org
* http://kitchen.ci

----

### Take a look at Kitchen Tests

```
nano test/integration/core/serverspec/core_spec.rb
```
```ruby
# ...
describe service('apache2') do
  it { should be_running }
  it { should be_enabled }
end
```


----

### Predict what will happen

**This may take 5 minutes the first time**

```
nano test/integration/core/serverspec/core_spec.rb
kitchen verify # includes 'create' and 'converge'
```
```ruby
# ...
describe service('apache2') do
  it { should be_running }
  it { should be_enabled }
end
```


----

### Do all of them currently pass?

**This may take 5 minutes the first time**

```
./run_tests
```

----

### We can fix this! W/ testing

1. Confirm our tests work as things stand now ✔︎
1. Create a feature branch
1. Write a _failing_ test, then
  1. Write the correcting code
  1. Retest, if failure, try again, else
1. Commit and submit PR


---

### Next: [Lab 4.2 TDD](lab_4.2-tdd.md)
