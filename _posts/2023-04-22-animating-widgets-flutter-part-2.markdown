---
layout: post
title: "Explicit Animations in Flutter 2"
date: 2023-04-22 20:23:00 +0000
categories: android, flutter
---

In the previous post, I explained how to get started with explicit animation in Flutter. In this post, I'll walk you through how to build a simple animation using all the classes I mentioned. We're going to make a hand-waving animation using the wave hand emoji.

### Setting up your project

Since the app is intended to only run on Android, I'll be using the flutter create command to only build the project for Android. Flutter builds a project for some default platforms(Android, IOS, Windows, Linux, Macos, Web); if you want to build for specific platforms, you can specify them using the platforms option.


`flutter create --platforms android wave_hand_app`


Clean up the default project template in your `main.dart` file, leaving only the `main` method and the `stateless widget class`. You should have something like this now afte converting your default class to a `stateful widget class`.


{% highlight liquid %}
{% raw %}

void main() {

    runApp(
        const MaterialApp(
            title: 'Wave',
            home: MyApp(),
        ),
    );

}

class MyApp extends StatefulWidget {

    const MyApp({super.key});

    @override
    State<StatefulWidget> createState() {
        return MyAppState();
    }

}

class MyAppState extends State<MyApp> {

    @override
    Widget build(BuildContext context) {
        return Text('hello world');
    }

}

{% endraw %}
{% endhighlight %}


### Using the animation classes

As said in the previous post, to use the `animation controller` class to build explicit animation, we need to first use the `Ticker` mixin. This class helps send a notification to the animation controller that a new frame has been rendered to the screen. We will use the `SingleTickerProviderStateMixin` because we only have one animation controller we intend on using to manage our animation.


{% highlight liquid %}
{% raw %}

class MyAppState extends State<MyApp> with SingleTickerProviderStateMixin { 
    ....
}    

{% endraw %}
{% endhighlight %}

Once this is done, we can go ahead and create and initialize our animation objects. Create instance variables within the state class.

{% highlight liquid %}
{% raw %}

class MyAppState extends State<MyApp> with SingleTickerProviderStateMixin { 

    late AnimationController _waveController;
    late Animation _waveAnim;
    late Tween _waveTween;

    @override
    void initState() {
        super.initState();
        // vsync is a TickerProvider interface and requires a class that
        // uses the TickerProvider mixin
        _waveController = AnimationController(
            vsync: this, 
            duration: Duration(milliseconds: waveDuration),
        );
        // the begin and end values were justified by how much further 
        // i wanted the hand wave animation to go on the z-axis.
        _waveTween = Tween<double>(begin: -5.0, end: 30.0);
        _waveAnim = _waveTween.animate(_waveController);
    }


    @override
    void dispose() {
        // releases the resources used
        _waveController.dispose();
        super.dispose();
    }

    ....

}

{% endraw %}
{% endhighlight %}




