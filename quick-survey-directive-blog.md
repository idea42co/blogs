# Quick Survey Directive Blog

The [quick-survey-directive](https://www.npmjs.com/package/quick-survey-directive) npm module is an easy and concise way to create a generate a survey! All you have to do is add 
the custom html element and specify the questions then bam! You have your survey ready to rock and roll. 
The inspiration behind creating this all stemmed from a co-worker of mine creating a simple mock up of a survey with some animations.
After seeing this mock up another team member of mine asked:

`"Why isn't there an Angular Directive I can just include that mimics this mock ups functionality?"`

From there I knew that I wanted to take that idea and turn it into a reality. The process for building the npm module was quite simple.
I stored all the functionality and scope variables of the module in the directive. To fully utilize angular with this idea
we choose to two way bind the answer property to the users input so it may always be updated in real time.
To achieve that we had to have the user set up a predefined structure on how the data will be specified and stored.
Design choices that we made were to include the whole template for the directive inside the directive's template property. We choose to do this 
because we didn't want to include another node module to handle xml requests for testing. Another design choice that we made was to set this up to easily
be hooked up to any database a user defines. Since the answer element in the predefined data structure is two way bound, setting up a `$watch` function
on it can prevent data from being lost on a page refresh by saving to a database within the `$watch`.

While creating the directive wasn't that difficult let's now talk about testing it. Testing the directive was an interesting process to say the least.
The directive I had not only had an anonymous controller to test but a link function as well. After several googles I was able to figure out how to test my 
unique directive. I'll quickly share with you some tips on how I wrote the test file but please feel free to look at the [test file](https://github.com/idea42co/quick-survery-directive/blob/master/test/unit/surevey-directive-test.js)
to see how I did it. When testing a directive that needs access to an attr on the element. Make sure that the included attr value is defined on the scope 
that you are currently working on. Another tip is to run `scope.$digest()` to make sure that your link functions are being run correctly.
Finally, my last tip to you is to just read the documentation on testing. If you take the time to learn what actually is going on instead of just
quickly grabbing the syntax, your test's will become better and in turn so will your application.

All in all this mini project was a lot of fun to take on. Not only did I learn a lot about node modules, but this was my first one that I ever published. My understanding of testing angular directives has improved a lot after working on this project. I hope other users will utilize my module to make their lives easier as it did mine. I yearn to create more variations of this survey, so expect more node modules coming from me soon!

