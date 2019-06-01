# UIKonf 2019

[Conference website](http://www.uikonf.com)

Berlin, 26th - 29th May 2019. 

18 talks on main stage plus two talks on second stage, at least four workshops.

__Organizers__: 
- [Sabine](https://twitter.com/sabinegeithner)
- [Chrissy](https://twitter.com/post4chrissy)
- [Engin](https://twitter.com/ekurutepe)
- [Engin](https://twitter.com/ekurutepe)
- [Bianca](https://twitter.com/biancawalty) 

# Resources

I enjoyed two great sets of SketchNotes to jog my memory:
- [Bruno Scheele](https://twitter.com/brunoscheele/status/1133710844049657856)
- [Felizia Bernutz](https://twitter.com/felibe444/status/1134143368706088960)

Videos of the talks will be on the official [UIKonf youtube channel](https://youtube.com/uikonf). Right now it contains recordings of the live streams. 

# Talks

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

Shannon told us about two small-ish bugs around gesture recognizing in OmniGraffle. Having to handle 18 different gesture recognizers got really unwieldly. So she began modelling gesture recognition as state machines, which allowed to simplify the code very much and enabled better reasoning about what was going on (because traditional debugging techniques do not go well with the real-time properties of gestures). 

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

Finally Sally concluded that although we are mostly striving to make Swift being used everywhere ([Chris Lattner jokingly set the goal of world domination](https://oleb.net/blog/2017/06/chris-lattner-wwdc-swift-panel/)), the strong focus on Apple hardware means you have to use an (expensive) Mac to write Swift using XCode. To make Swift more accessible we have to emphasize and work on other platforms like Raspberry Pi, Arduino, general Linux computers and more. 

[Slides from an older version of the talk at try! Swift conference Tokyo 2019](https://www.slideshare.net/mostgood/swift-hardware-hacking-try-swift)

## From Heroic Leaders To High Performing Teams

[Füsun Wehrmann](https://twitter.com/fuesunw) brings experience from working at Microsoft, Vodafone, Axel Spring and Xing and is now going to [Wayfair](https://www.wayfair.de). She experienced quite a development from the time around the [.com-era](https://en.wikipedia.org/wiki/Dot-com_bubble), when thoughts were still very influenced by [Taylorism](https://en.wikipedia.org/wiki/Scientific_management) with hierarchies, knowledge workers only in managment and _dumb_ executive teams to now where it feels like we are about halfway to where we need to be with high performing teams. Still so much is centered around having heroic leaders, which has just proven to be a wrong and unscalable idea. Younger people are demanding to bring their whole personality to work, not just a "professional self". Too much distance between planning and execution is too slow. 

So what helps us to make the next steps?
- customer centricity (take Apple, Google, Netflix as examples)
- people centricity (complex context cannot be managed hierarchically; improve diversity)
- shared leadership (reduce processs and rules, increase principles and consensus)
- collaborative mastery (focus on the team, not the individual)
- focus on value (look at outcomes and purpose)

We as developers have to remember that right now we are in high demand and are thus able to use our influence on the companies. 

## Swift 5 Strings

[Erica Sadun](https://twitter.com/ericasadun) was simply just amazing! Having enjoyed the party life in Berlin, she brought so much energy on stage and had the audience laughing while getting across a lot of content that at first glance might have appeared mostly technical and slightly boring. She talked about string interpolation in Swift 5. As the main goals of Swift are begin fast and safe by design, string interpolation is a surprisingly relevant topic. She demonstrated how classic string interpolation as we know it from C can lead to runtime crashes and is unable to catch errors at compile time ("Compile time errors make us stronger, runtime errors give us 1-star reviews"). A seemingly innocent simple and OK looking date formatter had 4 problems within 10 characters. The new way of doing it in Swift 5 is much closer to modern Swift syntax, much safer and more readable: ```"\(0x2a, toWidth: 6, radix: 16, prefix: true)" ```. You can provide smart string interpolation for your own types, can do padding, handling optionals and much more in a very safe, extensible and readable way. 

Memorable quotes:
- "Building developer tools is like a 3D printer for the mind"
- "Don't let your child date a format string. They are unsafe!"
- "I am here to warm up the crowd for Ellen Shapiro." ([in response to this]())
- A shoutout to Hamburg and Platt-speaking Germany: ["Moin"](https://twitter.com/ericasadun/status/1132928317047398402). 

## Kotlin/Native

[Ellen Shapiro](https://twitter.com/designatednerd) is an iOS and Android developer at [Bakken & Baeck](https://bakkenbaeck.no) and has done a lot of tutorials and books with [RayWenderlich.com](https://www.raywenderlich.com/u/designatednerd). She was brave enough to talk about Kotlin to a Swift-loving crowd and swayed many people (including me) from being kind of skeptical to "this is really interesting stuff" in her highly entertaining talk. 

So while writing cross-platform code is a highly controversial topic and a number of tools have come and gone, there remains business interest in doing so and while it is not really a thing to do Swift development on Android, she examined the state of using KotlinNative to also do iOS development. While Kotlin itself needs the Java Virtual Machine, so there is no direct way to use it on iOS, JetBrains created Konan to compile Kotlin into LLVM-Bytecode, that can be used on other LLVM-supported platforms like iOS. 

So she used Kotlin/Native for her project: [Porch Pirate Protector](https://github.com/bakkenbaeck/PorchPirateProtector) (inspired by [Package Thief vs. Glitter Bomb Trap](https://www.youtube.com/watch?v=xoxhDk-hwuo)). Part of the project would be a Raspberry Pi, a server, and apps for iOS and Anroid. 

Ellen went ahead and had to work around a (large) number of issues (use the right version of gradle (right now 5.3.1), huge folder structure, framework search paths, serialization not working as expected, create new objects instead of mutating variables, ....). We got a number of tips and hints to avoid pitfalls (don't mistake "kotlin-multiplatform" (what we want) with "kotlin-native-platform", Kotlin arrays and Swift arrays are very different, the same goes for enums ). If you worked around these, you can implement platform-specific function by using `expect fun` in Kotlin/Native and `actual fun` in platform code. Focus on what to write only once was the networking code (getting and sending JSON to the server) via [ktor](https://ktor.io) again with some caveats. She went on to talk about serialization, testing and much more. 

Increasing the speed in her already fast-paced talk, she did a fun impression of a box ring moderator and also managed to squeeze in some Cure lyrics. In summary, Kotlin/Native has come very far by now, but is still beta. 

[Slides](https://speakerdeck.com/designatednerd/native-in-practice-uikonf-berlin-germany-may-2019)

## A11y-oop - Adding new Accessibility Features to not-so-new Apps

[Alaina Kafkes](https://twitter.com/alainakafkes) is an iOS engineer at [Medium](https://medium.com). She talked about adding accessibility into existing apps and how important it is to create the right abstractions. Also: make specifications and seek feedback for them. Creating services that view controllers can subscribe to can make it more straightforward to update views for dynamic type or dark mode. These changes can only be made in a team-wide effort and can be a useful opportunity to improve the architecture.  

## Advanced Colors in iOS

[Neha Kulkarni](https://twitter.com/NehaPundlik) is an iOS engineer at [PlentyOfFish](https://pof.com/). Her talk about colors in iOS took us from the well-known RGB color space via sRGB to extended P3 colors with a wider color gamut. But colors are not only numbers, they have a meaning, so you should use semantic colors, which means that you do not specify black or green, but something like primaryText or headerLargeText. Namespaces can help structuring the colors (use folders in asset catalogs with this setting on). She warned us from going overboard - only the essential colors should be specified like this. 

In iOS setting colors should be done after viewWillAppear. In order to not repeat yourself and get into inconsistencies, you should share colors across bundles. To get completely dynamic, it is also possible to load colors from the internet. 

One should remember to not only use colors to distinguish something, but add contrast or symbols to help people with color blindness or people who change their display to monochrome. 

To assist the cooperation between engineers and designers, naming conventions should be used as well as clear specifications. And here as in many places early and frequent communication helps: "Have coffee with your designer"


## Promises in iOS

[Anne Cahalan](https://twitter.com/northofnormal) is an iOS developer at [Detroit Labs](https://www.detroitlabs.com/). She talked about the concept of Promises and Futures that are one main topic of discussion in Swift. The concept of a Promise in programming is very old but only now becomes mainstream. The idea is to have asynchronous tasks, where the promise represents the eventual result (or the error of the operation). What is mainly being done right now are handlers. From her view handler is a dirty word for an ugly concept (she delivered quite a rant, bashing the idea and usage handlers). Apart from being _unchainable_, handlers lead to unclean code.

As long as we don't have the proposed, but many times delayed `async/await` implementation in Swift, she recommended [PromiseKit](https://github.com/mxcl/PromiseKit) as a nice implementation for asynchronous programming. As alternatives she mentioned Google Promises, Brightfutures and Hydra. PromiseKit allows to describe asynchronous programming in a very readable way, similar to doing try/catch. Instead of handlers, the syntax looks more like

```
firstly {
	// networking
}.done {
	// update UI 
}.catch	{
	// error handling
}
```

You can wait for multiple promises to be fulfilled, ensure that certain conditions are fulfilled, acting as soon as one of multiple promises is fulfilled and much more. 

So while PromiseKit is not really light-weight, it can really help to make asynchronous code much more readable. Anne echoed that Erica mentioned "3D printers for the mind" with "Change your tools, change your mind".

## Muse Prototype Challenges

[Julia Roggatz](https://www.linkedin.com/in/jroggatz) impressed the audience by using an early alpha version of the software she was working on to do the whole presentation. She is a freelance iOS developer and currently working on Muse from [Ink & Switch](https://www.inkandswitch.com/). Muse is a virtual workspace for drawing, annotating and collecting with navigation through boards containing boards. It is completely rethinking the user interactions and thus deviates massively from Apples HIG (human interface guide). She started with the Apple Pencil and gestures instead of using any chrome (borders, toolbars). Different angles of the Pencil are used to distinguish between writing and moving. Using your fingers and the Pencil at the same time changes the action in a very direct way without needing to switch modes before an operation. 

A continuing hard challenge she discussed with the audience is doing the animations efficiently for big hierarchies. 

[Description of Muse](https://www.inkandswitch.com/muse-studio-for-ideas.html)

## What to expect when you are templating? Clue’s approach to Backend Driven UIs

[Kate Castellano](https://twitter.com/KateCastellano) is a senior iOS developer at [Clue](https://helloclue.com/) and talked about the way to drive the user interface with data from the server (backend driven UI). This allows much faster turnaround times on the UI (without going through code review, waiting for a new release) and do a lot of UI code for multiple platforms just once (on the server). Of course this needs carefully doing the generic templating code. Kate went to a number of challenges and provided a comprehensible way of communicating the UI as a sequence of segments from the server to the client (via JSON), apply the relevant logic and present it on the client. 

Finally she showed this working by changing the UI definition on the server live and watching the client reacting to it. To the already nerve-wracking live coding, Kate had to do it against a nearly empty battery - no pressure 😓

## Mobile && Me == It's complicated

[Lea Marolt Sonnenschein](https://twitter.com/hellosunschein) worked for Rent the Runway, provides popular content at [RayWenderlich](https://www.raywenderlich.com/u/leamars) delivered the final talk of the conference. And as usual it was a talk with a huge scope, asking the really big questions. She told us her story starting with programming apps during her education, being highly motivated and enthusiastic by what could be done. Working in business gave her a different perspective. She noticed that oftentimes the user is manipulated into doing things that were not her/his own benefit. She described dark UI/UX patterns being used to make it very hard for the user to do what was his/her interest, but much more easy or even necessary to do what the company behind the app wanted to happen. Another thing was the experience of not building lasting stuff: a lot of code never makes it into production and what gets in will soon be swapped out. Adding to it the irony of using tools on your phone to get less addicted to your phone. It's a consequence of the prevalent thought that "everything needs an app".

As a consequence of this she decided to get out of iOS and started her master on "Innovation Design Engineering" working with physical objects. While this can be very satisfying she also learned a lot about how easy to achieve many things are when working with code (undo, copy, test, debug and many more are much harder with physical objects).

Finally she told us about a trip to Africa, where she learned how much people relied on smartphones (kind of skipped the PC phase) and how much apps are essential tools (payment) instead of irrelevant gadgets. Here she found examples of how apps were actually the best way to solve very real problems. 

The takeaway was to consider our responsibility as developers to do the right thing for our users, to think about the impact our software makes on the world and be "a force of good".
