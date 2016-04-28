---layout: posttitle:  "Start Testing Any PHP Project in a Flash"date:   2014-05-23 12:37:00 +0100categories: php---I believe in Test Driven Development (TDD), as far as I have found it really improves your code. However, I don't think TDD is always feasible.I also work with a lot of legacy projects where it is really hard to get full test coverage, and test existing features. This is also difficultwhen you are working with a large framework e.g. an ecommerce platform which was just not built for this.
There is a really easy way to test these things however!
When building [Chula](http://github.com/stephcook22/chula) (the blogging platform which I use to base my blog on) we did not build it using TDD,we wanted to get things off the ground very quickly and I was working with someone who had been out of the PHP scene for a bit so didn't want toadd more complexity straight away. Once we got to a point where we could think about testing we started using Codeception's acceptance testing.
Acceptance testing is the kind of testing your clients would do, so in this case, can you post a blog or not.
It's very quick to write and only looks at the very top level.
For Chula we pull the codeception testing framework in through composer. This makes it really easy for anyone who pulls down the project to run the test.
We add them to our `require-dev` section like this:
{% highlight json %}
    "require-dev": {
        "codeception/codeception": "*",
        "codeception/phpbuiltinserver": "*",
    }{% endhighlight %}

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
                url: 'http://localhost'{% endhighlight %}

Make sure the url is the url of the home page of your app. This module will run the internal php server headless to do the tests. Note: No javascript will run when using this module.Look into the webdriver instead.
You can then use `php ./vendor/bin/codecept generate:cept acceptance Welcome` to create your very first test. This will create a file in `tests/acceptance` called `WelcomeCest.php`and will contain some basic bootstrapping to get you going.
Writing tests is really easy too:{% highlight php %}
    $I->am('User');
    $I->wantTo('see a list of posts');
    $I->amOnPage('/');
    $I->click('#list-posts');
    $I->see('This is how to create great posts in chula');
    $I->dontSee('wordpress-is-awesome');{% endhighlight %}
Set up what your test is going to do using the `$I->am` and `$I->wantTo` methods. These let codeception know what you are testing so it can include these details in its reports.Set up the starting state using `$I->amOnPage` and then start testing. The `$I->click` and other similar methods are there to let you navigate the page in the same way a user would,clicking buttons, filling in forms etc. The `$I->see` and `$I->dontSee` methods are similar to the assert methods in PHPUnit if you have used that. They perform the test. If eitherone of those statements fails it will fail that test.
You can find documentation for all available methods on codeception's [website](http://codeception.com/).
Now all you need to do is save the file and run `./vendor/bin/codecept run`. This will set up the PHPBrowser, load your site, run your tests and give you a result. The outputcodeception is also usually pretty good at explaining what's going on. It even takes screenshots and snapshots the html it sees when things fail. You can find these once youhave run a test in the `tests/_logs` folder. There is also a pretty html report of all your tests and how they faired for you to use. We use them in our continuous integration server.
I hope this has shown you how to get up and running with testing really quickly. My next blog (or two) will include some more advanced features of codeception which we havebeen using for Chula. Including codecoverage, abstracting tests and running tests in a browser.
Any thoughts? Post them [here](https://plus.google.com/+StephCook/posts/CRjZByNJacR) :)
