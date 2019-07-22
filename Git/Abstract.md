# Git for humans

# Abstract
There is no friendly way of versioning your information. Version control has developers in mind and is not welcoming for non-developers. An app with git. By providing an app that natively implements git everyone can have the full power of version control, without having to learn it.

# Problem
Tools used for version control and collaboration have software developers in their focus. For activities other than programming there are few options, and the ones available are scary to learn and to handle.

If we consider that any information that changes over time, regardless of its structure and format could be considered as a repository, then we can also visualise many other activities taking advantage of versioning these changes.


# Solution
Git is an app that strives to provide anyone with a version control system.
It is not meant for developers, although developers could also use it. The key points of the application is to make it easy and friendly to save state changes over time, review them, restore if necessary and merge collaborations.


# Defence
Git is build from the ground up fully natively with Swift. Requires zero dependencies and was developed with a user centric idea. Instead of trying to emulate git's command line tool functionality, it focuses on providing an interface friendly enough for everyone to allow them to have a repository of their information and have access to the full power of git.

By being fully native it can be completely independent from legacy libraries, which were build for different platforms, for the command line for example, and don't necessarily translate their applicability to an iPhone.

Implementing the functionality provided git' command line tool, we ensure standardisation, while some users could be using Git, other could be using a different tool if they prefer so. We call this git-fully-compatible.


# Related work
Most applications designed to version control focus on the software industry. They provide powerful features but at the same time they are packed with a high level of complexity.

Applications available on the App Store for MacOS rely on legacy libraries to implement git functionality, sadly this libraries limit most of the interaction and enclose the flow in a predeterminate manner, mostly defined for interaction over a command line.

Meanwhile some other applications try to leverage git implementation by communicating directly with git command line client. Unfortunately for them, because of sandbox restrictions, either they can't be published on the App Store or they rely on the users to setup manually the whole environment, which is fine for developers, but not easy to do for non-developers.

On iOS we have an even darker spectrum of possibilities as there is no command line tool available, the few applications that provide version control capabilities rely on legacy libraries and unfortunately they aim to emulate a command line tool, instead of providing an iOS experience.


Git is the first documented attempt to implement git's command line tool fully natively with Swift.
The source code is Open Source and available on Github.
It is available on iOS App Store and on the MacOS App Store, and it is for free.

Unfortunately, being an indie developer, and the project being Open Source and available for free on the App Store I would require travel assistance to be able to speak at iOS Conf SG 2020.
