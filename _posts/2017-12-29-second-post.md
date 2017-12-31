---
layout: post
comments: true
permalink: /blog/:title
title: Second Post
---

If you make your foundations strong, then you can rise high and touch the sky.
Android framework does not advocate any specific way to design your application. That in a way, make us more powerful and vulnerable at the same time.
Why am I even thinking about this, when I am provided with Activity and I can, in essence, write my entire implementation using few Activities?
Over the years writing code for Android, I have realized that solving a problem or implementing a feature at that point of time is not enough. Your app goes through a lot of change cycles and features addition/removal. Incorporating these over a period of time creates havoc in your application if not designed properly with separation of concern. That is why I have come up with a guide that I follow religiously for all my architectural designs from the very single code I write for that application.
The principles presented in the MVP philosophy is by far the best I have come across.
What is an MVP and why should we explore it?
Let’s take a ride into the past. Most of us started creating an Android app with Activity at the center and capable of deciding what to do and how to fetch data. Activity code over a period of time started to grow and became a collection of non-reusable components. We then started packaging those components and the Activity could use them through the exposed apis of these components. We started to take pride and began breaking codes into pieces as much as possible. Then we found ourselves in an ocean of components with hard to trace dependencies and usage. Also, we later got introduced to the concept of testability and found that regression is much safer if it’s written with tests. We felt that the jumbled code that we have developed in the above process is very tightly coupled with the Android apis, preventing us to do JVM tests and also hindering an easy design of test cases. This is the classic MVC with Activity or Fragment acting as a Controller.
So, we formulated few principles that solved most of the above-mentioned problems if implemented carefully. Those principles, we call as MVP (Model-View-Presenter) design pattern.
What is an MVP design pattern?
MVP design pattern is a set of guidelines that if followed, decouples the code for reusability and testability. It divides the application components based on its role, called separation of concern.
MVP divides the application into three basic components:
Model: It is responsible for handling the data part of the application.
View: It is responsible for laying out the views with specific data on the screen.
Presenter: It is a bridge that connects a Model and a View. It also acts as an instructor to the View.
MVP lays few ground rules for the above mentioned components, as listed below:
A View’s sole responsibility is to draw UI as instructed by the Presenter. It is a dumb part of the application.
View delegates all the user interactions to its Presenter.
The View never communicates with Model directly.
The Presenter is responsible for delegating View’s requirements to Model and instructing View with actions for specific events.
Model is responsible for fetching the data from server, database and file system.
The above-mentioned principles can be implemented in a number of ways. Each developer will have its own vision of it. But in the nutshell, basic nuts and bolts are common with minor modification.

With great power, comes great responsibility.
Now, I lay down the preamble, I follow for MVP.
Activity, Fragment, and a CustomView act as the View part of the application.
Each View has a Presenter in a one-to-one relationship.
View communicates with its Presenter through an interface and vice versa.
The Model is broken into few parts: ApiHelper, PreferenceHelper, DatabaseHelper, and FileHelper. These are all helpers to a DataManager, which in essence binds all Model parts.
Presenter communicates with the DataManager through an interface.
DataManager only serves when asked.
Presenter does not have access to any of the Android’s apis.
Now, all these information can evidently be found on any blog or Android guide for MVP. Then what’s the point of this article?
The reason that this article is written is to solve a very important challenge with MVP. How to actually implement it as an entire application?
MVP appears to be very simple when explained with a simple Activity example but makes us feel lost when we try binding all the components of an application together.

If you want to dive deep into a world of beautiful coding and be mesmerized then follow along with this article. It’s not a news article, so get involved with it, put on your shoes with your back straight and away from all distractions.

Let’s sketch the blueprint of the architecture first.
[Android architecture]({{ site.url }}/assets/arch.png)[^fn-footnote_two]

 Architecture is the first thing you should work on for any software. A carefully crafted architecture will minimize a lot of rework in future while providing the scalability ease.
 Most of the project today is developed in a team, hence the code readability and modularity should be taken as utmost important elements of the architecture.
 We also rely heavily on 3rd party libraries and we keep switching between alternatives because of use cases, bugs or support.
 So, our architecture should be designed with plug and play design. The interfaces for classes serves this purpose.




[^fn-footnote_two]: [Android architecture](https://developer.android.com/topic/libraries/architecture/index.html)
