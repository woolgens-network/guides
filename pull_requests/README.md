# Pull requests

In order to write and maintain clean code we use a pipeline that automatically checks your code for errors before getting merged into our `master` branch.
This is done with a platform called [Drone](https://www.drone.io/). Our drone instance can be found under https://drone.woolgens.net. You can register and login
via your GitHub account, after joining our organisation. You will then have permissions to view all builds.

## Tests

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

## drone.yml

In order to configure our pipeline every repository will have a `.drone.yml` file, in which the pipelines are written. If you are starting a new repo you can find
a few example drone pipelines under `woolgens-network/guides/pipelines`. 

## Pull request

Every developer will be programming on a branch other then the `master`. For example, I want to create a new feature allowing users to execute the command "/food"
and then recieving an apple in their inventory. I would create a new branch called "create-food-commmand" and do all of my edits in that branch. 

After finishing my feature I will then push the branch to the origin and create a new Pull request. This can easily be done over the GitHub UI when you go to the
pull request section of the corisponding repository. There you can then reference any issues that might be linked and give a brief overview of what you did.

Once you create the pull request our pipeline will run, testing your code. Once the pipeline finished you can then get a code review from one of our
Senior developers. They may ask you to change some things about your code and once they are happy our feature will be merged into the master branch. 
