# UIKonf 2019

[Website](http://www.uikonf.com)

Berlin, 26th - 29th May 2019. 

18 talks.

## Inclusive and Accessible App Development

[Kaya Thomas](https://twitter.com/kthomas901) has been at Apple, where she helped making XCode more accessible for blind developers, then worked at Slack and now at [Calm](https://www.calm.com).

- __What__ are accessibility and inclusivity?
	+ accessibility: building apps usable for all people 
	+ inclusivity: welcome all kind of people as being part of a whole, make everybody feel like they belong
- __Why__ should we care?
	+ business reasons 
	+ because it's the right thing to do 
	+ going the extra mile can make a __huge__ difference for some people
- __How__ do we provide it?
	+ focus groups 
	+ third party audits 
	+ should be a blocker for release

## Detangling Gesture Recognizers

[Shannon Hughes](https:/twitter.com/whattherestime4) works at the [Omni group](https://www.omnigroup.com). She gave an example how some seemingly small bugs can lead to a larger re-architecturing of an app and provide a much better path into future developments. For me it emphasized one major learning in software development: if bugs are found, not only fix them (and of course add a unittest for replicating them so you catch them when they reappear) but look around at the context. This bug might tell you something important about your code - the architecture might not fit, there might be some false assumptions around or just that the code around this bug is somehow sub-par. 

Shannon told us about two small-ish bugs around gesture recognizing in OmniGraffle and how modelling gesture recognition as state machines allowed to simplify the code very much and allowed better reasoning about what was going on (because traditional debugging techniques do not go well with the real-time properties of gestures). 

## Rolling your own Network Stack

[Glenna Buford](https://twitter.com/glennersboofy), working for [8fit](https://8fit.com) and [coup](https://joincoup.com/) had one example of what for me became a recurring topic: instead of just selecting the most popular third-party library for something and adding a dependency, think about writing your own smaller code for just the thing you need. In this case, instead of using something like [AlamoFire]() and also instead of just a naive implementation based on NSURL* she created a small structure with an APIRouter, NetworkService and NetworkOperation. It was a good demonstration of using different Swift language feature to create a really nice and usable basis for common tasks.

[Slides](https://speakerdeck.com/glenna/rolling-your-own-network-stack)

[Code](https://github.com/glenna/NetworkStackExample)

## Declarative Presentations

[Nataliya Patsovska](https://twitter.com/nataliya_bg) is a software developer at [iZettle](https://izettle.com) and previously worked at [Spotify](https://spotify.com). She explained the difference between imperative and declarative presentations and how to do the latter without something huge like [Flutter](https://flutter.dev)) or [React Native](https://www.reactnative.com) outside the world of Swift/UIKit. Instead she used the [Presentation framework](https://github.com/iZettle/Presentation) and did some very brave and impressive live coding. The idea is to regard view presentation as an asynchronous function and thus describing it as a declarative inferface with Promises/FutureResult. Among the advantages of working this way are improved testability and hiding some complexity.

[Slides](https://www.slideshare.net/NataliyaPatsovska/declarative-presentations-uikonf)

[Playground](https://github.com/nataliq/DeclarativePresentations)

## Internationalizing your App

[Kristina Fox](https://twitter.com/krstnfx) who is a senior iOS engineer at [Intuit](https://www.intuit.com/) showed us in her highly polished talk that internationalization is about more than just translating the user-facing strings into another language. One striking example outside apps was that food taste is regionally different, so that Pixar [changed some food](https://www.reddit.com/r/MovieDetails/comments/b7dn4d/in_inside_out_the_pizza_toppings_were_changed/) shown in Inside Out depending on the region to maintain the same meaning/effect. You also have to consider things like brands, different units (Fahrenheit vs. Celsius or currencies). 

To do it right, one should do user research and try to __watch__ them doing something, instead of just asking ("What people say they do and what they actually do is usually different").

Beyond showing how to do good i18n, she also demonstrated some limits of current technology, how to test your i18n, using pseudo-languages and finally how to decide, if and how you maybe should remove a particular language/region from your app.  

Also: don't forget right-to-left languages.

[Slides](https://speakerdeck.com/krstnfx/internationalizing-your-app)


## Mockolo: Efficient Mock Generator for Swift

[Ellie Shin](https://twitter.com/ellsk1) is a Senior iOS Engineer at [Uber](https://www.uber.com/) talked about efficient code generation in Swift. Generating mocks is helpful for testing but tedious to write by hand and may be too slow, when doing it for large codebases with existing tools. Ellie walked us through a number of those challenges and how she developed Mockolo (soon to be found on [github](https://github.com)) at Uber carefully find a way to effectively parallelize the process, deciding on the right parsing engine and many more. 

## Consistency Principle

[Julie Yaunches](https://twitter.com/julieyaunches) tackled the problem of codebase longevity and sustaining a high velocity on a codebase. More or less the holy grail of software development. Beside the usual patterns, rules and recommendations, she developed the consistency principle as a guiding light for development. One main thing that leads to _rotting_ codebases that are difficult to understand and adapt are duplicated verticals. What usually happens is that at the start of the project you decide on a clean architecture with separate layers and a small number of technologies/frameworks/libraries/patterns for each layer. As time goes on, technical necessities, new people, and new ideas lead to the introduction of more patterns per layer. The problem is that most times one pattern is not completely replaced by another one but instead it is used for some parts, so both patterns co-exist. As this process goes on, to change something in one layer you have to understand and change multiple patterns/approaches. To avoid this she recommends not to "never change" but to view each layer as its own API and change the pattern once and for all so that the old one can be easily completely replaced. 


## How to Market Your Mobile App

[Lisa Dziuba](https://twitter.com/LisaDziuba) from [flawless](https://flawlessapp.io) showed us how to market a mobile using flawless as an example. After the initial release in 2017 was disappointing ("build something and they will come" does not really work), they made more deliberate attempts with updates later on. First thing to focus on is to get to know your potential users/customers. Build personas, but check your underlying hypothesis using interviews, online discussions, ask in your app or go to events. Your design statement will be the result from modelling your users, learning about your competitors and your own motivation. Start with as much free marketing as you can get to improve and optimize your marketing message before you put money behind distributing it. Free marketing might be blogs, giveaways, contacting influencers, contacting media and much more. Before your public launch research the channels you might want to use and have a plan to execute quickly, for example on [Product Hunt](https://www.producthunt.com). Paid marketing can then be done via ads, sponsorships, doing SEO and ASO. It is important to measure the impact and adjust your strategy. Doing a talk at a developer conference about marketing an app and using an app for deverlopers as an example might be considered an efficient way to do marketing. 

## Swift to Hack Hardware

[Sally Shepard](https://twitter.com/mostgood) took us on a trip to see Swift being used beyond the Apple ecosystem in a cat-oriented talk about a fun project. First she looked at using Swift on a [Raspberry Pi](https://raspberrypi.org), connecting a digital scale HX711 and computing the value of coins from their weight, working with [SwiftyGPIO](https://github.com/uraimo/SwiftyGPIO), displaying data on a small LCD display using [HD44780LCD](https://github.com/uraimo/HD44780CharacterLCD.swift). This took us from the world of analogue signals and reference drivers written in C all the way to the nice world of Swift again. The resulting data should be uploaded to a server, so here she used [Kitura](https://www.kitura.io) and [KituraKit](https://github.com/IBM-Swift/KituraKit) on Linux. Finally, the corresponding iOS app was of course also written in Swift (no surprise here).

Finally Sally concluded that although we are mostly striving to make Swift being used everywhere ([Chris Lattner jokingly set the target of world domination](https://oleb.net/blog/2017/06/chris-lattner-wwdc-swift-panel/)), the strong focus on Apple hardware means you have to use an (expensive) Mac to write Swift using XCode. To make Swift more accessible we have to emphasize and work on other platforms like Raspberry Pi, Arduino, general Linux computers and more. 

[Slides from an older version of the talk at try! Swift conference Tokyo 2019](https://www.slideshare.net/mostgood/swift-hardware-hacking-try-swift)

## From Heroic Leaders To High Performing Teams

[Füsun Wehrmann](https://twitter.com/fuesunw)

## Swift 5 Strings

[Erica Sadun](https://twitter.com/ericasadun)

## Kotlin/Native

[Ellen Shapiro](https://twitter.com/designatednerd)

## A11y-oop - Adding new Accessibility Features to not-so-new Apps

[Alaina Kafkes](https://twitter.com/alainakafkes)

## Advanced Colors in iOS

[Neha Kulkarni](https://twitter.com/NehaPundlik)

## Promises in iOS

[Anne Cahalan](https://twitter.com/northofnormal)

## Muse Prototype Challenges

[Julia Roggatz](https://www.linkedin.com/in/jroggatz)

## What to expect when you are templating? Clue’s approach to Backend Driven UIs

[Kate Castellano](https://twitter.com/KateCastellano)

## Mobile Applications in Africa

[Lea Marolt](https://twitter.com/hellosunschein)


# Resources

I enjoyed the great [SketchNotes](https://twitter.com/brunoscheele/status/1133710844049657856) from [Bruno Scheele](https://twitter.com/brunoscheele) to jog my memory. 

Videos of the talks will be on the official [UIKonf youtube channel](https://youtube.com/uikonf). Right now it contains recordings of the live streams. 
