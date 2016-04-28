---
There is a really easy way to test these things however!
When building [Chula](http://github.com/stephcook22/chula) (the blogging platform which I use to base my blog on) we did not build it using TDD,
Acceptance testing is the kind of testing your clients would do, so in this case, can you post a blog or not.
It's very quick to write and only looks at the very top level.
For Chula we pull the codeception testing framework in through composer. This makes it really easy for anyone who pulls down the project to run the test.
We add them to our `require-dev` section like this:
{% highlight json %}
    "require-dev": {
        "codeception/codeception": "*",
        "codeception/phpbuiltinserver": "*",
    }

Once you have used composer to install your dependencies you can use `php ./vendor/bin/codecept bootstrap` to create the files needed for codeception to run in your project.
This command should generate the tests folder in your project root and a `codeception.yml` file. This exposes some general config for the codeception install.
Inside the tests folder the bootstrap will have also created 3 more config files. `acceptance.suite.yml`, `functional.suite.yml` and `unit.suite.yml`. I will only look at the acceptance.suite.yml for now.
The acceptance.suite.yml contains some config just for the acceptance tests. To start with you will probably only need the `PhpBrowser` module enabled. Like this:
{% highlight yaml %}
    class_name: WebGuy
    modules:
        enabled:
            - PhpBrowser
        config:
            PhpBrowser:
                url: 'http://localhost'

Make sure the url is the url of the home page of your app. This module will run the internal php server headless to do the tests. Note: No javascript will run when using this module.
You can then use `php ./vendor/bin/codecept generate:cept acceptance Welcome` to create your very first test. This will create a file in `tests/acceptance` called `WelcomeCest.php`
Writing tests is really easy too:
    $I->am('User');
    $I->wantTo('see a list of posts');
    $I->amOnPage('/');
    $I->click('#list-posts');
    $I->see('This is how to create great posts in chula');
    $I->dontSee('wordpress-is-awesome');

You can find documentation for all available methods on codeception's [website](http://codeception.com/).
Now all you need to do is save the file and run `./vendor/bin/codecept run`. This will set up the PHPBrowser, load your site, run your tests and give you a result. The output
I hope this has shown you how to get up and running with testing really quickly. My next blog (or two) will include some more advanced features of codeception which we have
Any thoughts? Post them [here](https://plus.google.com/+StephCook/posts/CRjZByNJacR) :)