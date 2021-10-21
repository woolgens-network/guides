# Woolgens Quick Start Development guide

**Table of contents:**

1. [ Naming ](#naming)
2. [ Versions ](#version)
4. [ Tests ](#test)
3. [ Pull requests ](#pull)
4. [ Github Issues ](#issues)


<a name="naming"></a>
# Naming
The first step in creating a new project is to determine the naming scheme. As a simple rule of thumb please use the below given schema:

- `{name}-plugin` when you are developing a Minecraft or Proxy plugin
- `{name}-service` when you are developing a micro service
- `{name}-page` when you are developing a web application

_Replace {name} with the name of the project. This name will be the name you should use on all references to the project._

### Choosing a name
The name of your project should be **short**, **descriptive** and **understandable**.

We want to avoid long names, as they become harder to read and may cut of in certain programs. Therefore we ask you to _ONLY_ use long names
when there is no alternative name available. 

If that is the case please write multiple words in one line _without_ spacing.

Example: `jumpandrun-plugin`

## Java specific conventions
Please set your _groupId_ to `net.woolgens` and **NOT** your personal _groupId_.

_Remember: The code you develop for woolgens is not your own. It belong to the network and therefore it should be named accordingly._

<a name="version"></a>
# Versions

We use [`Semantic Versioning 2.0.0`](https://semver.org/)

Given a version number `MAJOR.MINOR.PATCH`, increment the:

- `MAJOR` version when you make incompatible API changes,
- `MINOR` version when you add functionality in a backwards compatible manner, and
- `PATCH` version when you make backwards compatible bug fixes.

<a name="test"></a>
# Tests

One vital part of using a CI pipeline is writing tests. The details vary from language to langage, but the process and concept stays the same. When developing
a new feature first write a set of tests, that are prewritten to recieve the correct outcome. As an example:

```js
/* 
    We want to write a function that multiplys 10 and 2.
    The outcome has to be 20 so we can begin by writing out test.
    After writing our test we can then implement the final logic behind the test. 
    Once all tests run we can then push and create a pull request.
*/

const multiply = (num1, num2) => {
  return num1 * num2;
}

describe('Demo Test', () => {
    it('Multiplies 10 and 2', () => {
        const result = multiply(10, 2)

        expect(result).toBe(20)
    })
})
```

This example was written in Javascript with Jest. However the concept is the same in other programming languages. Every repository will have tests pre configured,
making it easy to add new ones. 

More information about Test-driven development: 
- https://en.wikipedia.org/wiki/Test-driven_development
- https://www.youtube.com/watch?v=Jv2uxzhPFl4&ab_channel=Fireship

## Drone.io

In order to configure our pipeline every repository will have a `.drone.yml` file, in which the pipelines are written. If you are starting a new repo you can find
a few example drone pipelines under [`woolgens-network/guides/pipelines`](https://github.com/woolgens-network/guides/tree/master/pipelines). 

More information about [Drone](https://readme.drone.io/)

<a name="pull"></a>
# Pull requests

In order to write and maintain clean code we use a pipeline that automatically checks your code for errors before getting merged into our `master` branch.
This is done with a platform called [Drone](https://www.drone.io/). Our drone instance can be found under https://drone.woolgens.net. You can register and login
via your GitHub account, after joining our organisation. You will then have permissions to view all builds.

Every developer will be programming on a branch other then the `master`. For example, I want to create a new feature allowing users to execute the command "/food"
and then recieving an apple in their inventory. I would create a new branch called "create-food-commmand" and do all of my edits in that branch. 

After finishing my feature I will then push the branch to the origin and create a new Pull request. This can easily be done over the GitHub UI when you go to the
pull request section of the corisponding repository. There you can then reference any issues that might be linked and give a brief overview of what you did.

Once you create the pull request our pipeline will run, testing your code. Once the pipeline finished you can then get a code review from one of our
Senior developers. They may ask you to change some things about your code and once they are happy your feature will be merged into the master branch. 

<a name="issues"></a>
# Github Issues

### Why?

Issues in area documentation is a very strong feature what Github gives us.
In it it is possible to write down content and divide it into sections and connect them. (example linking: #1)

Among other things, it is possible to describe and manage bugs well.


### Format

#### Sprint

```
** Summary **

** Sprint Sections **
  - [ ] Section task 1 (#1  // link other issues)
  - [ ] Section task 2
```

Example:

```
In this sprint the development environment must be available and 
the possibility to start directly with the content of the respective project.

Sprint 1:
  - [ ] Create project scaffold (#1)
  - [ ] Add necessary dependencies to pom.xml
  - [ ] ...

```

#### Section
```
** Description **

** Tasks **
  - [ ] Task 1
```

Example:

```
Create project scaffold with the java version 16.

Tasks:
  - [ ] Create quarkus project with the given name "example"
  - [ ] ...

```

### Conclusion

Try to use the github issue function more often to create TODO lists as an example.

Write down your concepts there as well.
