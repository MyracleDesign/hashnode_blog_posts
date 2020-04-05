## Flutter Mobile: Scrum Poker App

Welcome to my story, how I created a Scrum Card App with flutter in one day. With this article, I want to show you how simple it can be to create a flutter app. My challenge was to create a minimal app in a short time.

First, I want to start by creating a clear picture of what we want to achieve. I work currently on a Scrum Team, we always have to carry around our cards for sprint poker. These cards are old, dirty and very often used from a lot of teams and so I decided to change that with an app, once and for all.

# Scrum Poker
If you have never worked in a Scrum Team before, you maybe never heard the term Scrum Poker. To explain the whole idea, would probably be too much for that story, but if you are interested  [Ravindra Prasad](https://medium.com/@ravindraprasad) wrote an excellent  [article](https://medium.com/@ravindraprasad/story-point-estimation-and-planning-poker-3a0938a6b5ca) about that topic.

> It is like real poker, but everyone has the same cards.

![dogCards.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1569493502425/8yPsFtjf6.gif)  
Credits to  [Giphy](https://giphy.com/gifs/dog-poker-playing-httS0Xzi9ZMQ0) 
# Visual guidance
For me, it is always helpful in my projects to have visual guidance like a prototype. This prototype can be a drawing on a paper or a fully-fledged prototype. For this article, I created a quick prototype in Adobe XD just to show you how it can look like and to give myself visual support.

![1_2lpaIgBAylxtKU8RJONtRA.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1569277115900/n9mA5wY7Y.gif)

With that, we have a prototype and now we know what we want to create. Now we are ready for development. First of all, we have to create a new project with Flutter. On the  [Flutter Website](https://flutter.dev/), there are more information on how to set up your environment. I will use for this story  [Android Studio](https://developer.android.com/studio/)  with the Flutter and Dart plugin.

# Restructure our boilerplate
After the setup of the flutter project, let us start with removing all the comments that we do not need. I separate the Home Page from the main file so that we have a better feeling for our application.  With that, we bring a bit more order in the project boilerplate.
In our main file, this is what should remain.

![MainDartAfterCleanup.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1569493453904/pDC-vkAKn.png)

In the "myHomePage.dart" you will find the Stateful "MyHomePage" Widget that is initialized with the flutter project.

![HomePageCleanup.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1569493425003/trxqylxVU.png)

And the following image should be the folder structure.

![folderStructure.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1569493405528/cPoU3HyRm.png)

## Our HomePage
For our first shot, we want to use the existing Scaffold of the HomePage. This contains our scrum cards and a Flutter GridView. The GridView gives us the option to align multiple items in a grid. The count constructor of the GridView provides us, with the out-of-the-box functionality, to create our Grid with Cards. 

![Scaffold.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1569493364167/p_0RHc1sx.png)

First, we initialize a variable "Fibonacci" so that we can contain the numbers in an array. If you take a closer look into the children of the count constructor of the GridView you can see the "for Loop". Is this not great? We can loop inside the children array to map our Fibonacci array to placeholders.

![Placeholders.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1569277380123/9C1csC_kl.png)

Great, the Grid looks already very promising. Did you see how the Placeholder widget is handy in this part? With that in place, we do not have to create anything for the card just yet. However, the result is already evident. The Placeholders help us to structure already our app without actually implementing something.

## The Cards
Now that we have the basic structure in place, we have to think about how we want to display our Cards. Thankfully Flutter provides already something for us. The Card Widget will help us to create excellent visualization of the cards with Text inserted. Because the cards will not change, we can create a stateless widget for it with an icon or a number. For now, it will live in the "MyHomePage".

![CodeImageScrumCard.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1569493313365/TNKPAfe_3.png)

![GridView.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1569493341489/UCaS0c9o1.png)

![Scrum.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1569277456334/lRzzufTC_.png)

## Gestures
Now it is time to control our behaviour of the app. When we tap a card, it should remove the widgets from the tree and replace it with a single card widget. That, however, changes the state of the "MyHomePage" Widget.

To achieve that tap behaviour, we first have to surround our Card element with a GestureController. After that, we have to specify the onTap event inside of the card.

![Code GestureDetector.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1569493272169/0G5cjdFxy.png)

This will now print every click on a card in a separate line in the console.
 
![imageprint.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1569493240690/yCLTASFE2.png)

# Downtime
![Ineedabreak.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1569492928929/GrbvTIcCY.gif)

Credits to  [Giphy](https://giphy.com/gifs/break-i-need-a-RiWZUGcZPEKdQgrQ96) 

Alright, we made it very far already. So let's take a break and recap shortly, what we created already.  

- a Design for our Scrum Card App
- a HomePage
- a ScrumCard widget
- Gestures and tapping event

The next thing that we need to do is to change the state of our app, after a tap.
Whenever a card is tapped we want to replace the Body from the HomePage with a Big ScrumCard Widget.

Now comes the tough part so. Therefore make yourself ready, take a deep breath and then let's get into it!

![deep-breath.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1569492352663/pNDoFfP0T.gif)

Credits to  [Giphy](https://giphy.com/gifs/angrybirds-angry-birds-matilda-the-movie-l0K4jwyp6FZa9phyU)

# State Management
There are two different kinds of Widgets in Flutter.

1. Stateless Widgets
2. Stateful Widgets

The stateless widget is a widget that will always be shown according to its initial values. During its lifetime the initial values can not change. The stateful widget, on the other hand, contains a real state and if you change the state the widget will be re-rendered. If you want to read more about the different types of widgets feel free to take a look at the [article](https://proandroiddev.com/flutter-a-hitchhiker-guide-to-stateless-and-stateful-widgets-cc9f9295253b) by [Deepak K](https://proandroiddev.com/@DakshHub).

Now we have to first time handle the state of our widgets. When we click the button the state of the "Grid Widget" should change to a big "Card Widget". This tells us that we have at least two different states in our app. To keep track of these states we have to change our current "Stateless" Widget to a "Stateful" Widget. The easiest way is to click on Stateless Widget and use the IDE function to change the Stateless Widget to a Stateful Widget.

![StatelessToStateFul.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1571347946225/quClvBudv.png)

Because the new Widget is now stateful, we can change its value and the "build" method can react to these different states. 

![stateVariables.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1569491729143/M-sW_HpG3.png)

We want to track the information of the Icon that we want to show or the Text that is visible on the card so we need that to a state. I call that variables "singleCardText" and "singleCardIcon". Additionally, I want to have a boolean that knows if I have to show the Main Page with all Cards or just the Single Big Card.

Be careful at that point, I made here a big mistake and put all these variables in the build method. The build method gets called multiple times and whenever it gets called it overwrites the values again.

![mistake.jpeg](https://cdn.hashnode.com/res/hashnode/image/upload/v1569491709301/OJRHdMz_L.jpeg)

Of course, that sounds trivial but cost me 1 hour of my lifetime.

# The Exchange

Now we want to swap the widgets based on the "isHomePage" value. Therefore we can use one of Flutter skills. We surround our GridView.count constructor with an ternary operator.
That checks our isHomePage and add the respective Widget to the Container.

![isHomePageGridViewPadding.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1569491640586/5hd4hHZmp.png)

If you get confused by the "?" and the ":" in the code I can recommend you to read an article about ["Ternary Operator"](https://medium.com/flutter-community/simple-and-bug-free-code-with-dart-operators-2e81211cecfe) from [Deven Joshi](https://medium.com/@dev.n).
With that in place, we have the opportunity to change the "isHomePage" to false and it would show us only the Padding (and whatever is there inside) or we keep it on true, and it will show us the GridView. Therefore we need the "setState" method. It will allow us very easy to change the current state of the widget.

![switchToCard.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1569491604892/flmEoYLvA.png)

Great so far. Now instead of the tap where we just print something in the console, we want to execute the "switchToCard" method.
But how? The method has to live in the _HomePageState and the ScrumCard has no access to that state? Alright then, let me explain it to you because there is a fairly simple solution to that problem. We just pass our function into the ScrumCard Widget. And whenever the user taps now on the card we call that method and "notify" our parent widget.

![buildGesture.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1569491286445/jnbYyCD33.png)

![scrumcard.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1569491302368/sANwu6NTG.png)

If you take a brief look into the code snippets you can see that the ScrumCard calls the notifyParent method, which in fact is the switchToCard method. This should help us now to transform from a grid with multiple scrum cards, to a single big one and Vice Versa. Now there is only one step left, we have to create a beautiful Card UI that will be generated when the isHomePage is false.

![Screen Shot 2019-09-26 at 9.43.45 PM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1569491047971/c5njQApoU.png)

As you most likely already discovered I added here another function for notifyParent so that we can swap back to the HomePage.

Now the switch of card and grid should work already. To improve our app even more we can use the "[AnimatedSwitcher](https://www.youtube.com/watch?v=2W7POjFb88g)". I found this amazing video from the flutter team and that is a perfect use case. The AnimatedSwitcher, as you maybe have already guessed, helps us to swap two widgets with each other. It adds a smooth transition between these two and this looks much more friendly. You just have to put your ternary operator in between as a child and give it a Duration how long the transition should take.

![Screen Shot 2019-09-26 at 9.43.08 PM.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1569490997840/mhuNvfVKG.png)

Ok, so let's run our simulator or emulator and take a look how the app looks now.

![Finished_Scrum_Cards.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1569490563172/xQXN94bq6.gif)

# What's next
This is now an app that already solves one important problem in software engineering.
From now on I do not have any more to carry real cards from one room to another. Never again I will have to grab old smelly cards and show them to my Product Owner. We do not want to know which liquids touched those filthy cards…

This is of course just the beginning. With the knowledge that we got during this session, we can do much more. This app shows how easy it is with flutter to create a nice fully functional app.

Now it is your turn. My challenge for you till my next article is, to create this app or fork my [repository from GitHub](https://github.com/MyracleDesign/flutter_scrum_cards) and extend this app by a small additional functionality. To give you some examples that you could add,

* Make it possible to change from Fibonacci numbers to other Scrum Poker numbers
* Create a history of the selected cards
* Make a custom Animation between the transitions

And if you are finished spread the word and let everyone know how cool Flutter and our community is! I am already curious to see all the beautiful results.
If you have any feedback let me know and if you are interested in other cool articles, feel free to follow me on [Twitter](https://twitter.com/max_myracle) or take a look into my GitHub Repository.

%[https://github.com/MyracleDesign]

%[https://www.buymeacoffee.com/sBGXj7Pl4]