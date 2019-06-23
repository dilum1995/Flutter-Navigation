![cover](other/cover.png)

## Flutter Navigation 

Under flutter navigation we will be disscussing following sub topics.

1. How screens are stacked in Flutter.
2. How to navigate back and forth among screens.

	2.1 Simple Routing 
	
	2.2 Named Routing 
	
3. How to send data back and forth while navigating among screens.

	3.1 Data passing while simple routing 
	
	3.2 Data passing while named routing  

### 1. How screens are stacked in Flutter
In flutter we identify screens as **'routes'** so, if we are talking about the home screen or the first screen, we are refering to the first route or the initial route of our application. So, a Route is an abstraction for a “screen” or “page” of an app.

Flutter has provided **[navigator widget](https://api.flutter.dev/flutter/widgets/Navigator-class.html)** and its methods to naviagate among screens. Furthermore in flutter **navigator widget** maintains all the **routes** (screens) as stack. Also, as we all know stacks follow the concept of **LIFO** /Last In First Out. In Flutter also we have the same concept to manage the screens/routes stack

Basically, when you lunch the **first screen or route in Flutter**, In case of **android this route is know as activity** and in **iOS** it is known as **ViewController**.


![cover](other/HowscreensarestackedinFlutt.gif)

#### 2.1 Simple Routing 
If you want to [navigate to new page or if you want to navigate back to the previous page/route/screen](https://flutter.dev/docs/cookbook/navigation/navigation-basics) we user methods which has been exposed by the Flutter Navigator class/widget.  So, **push and pop** are the simplest methods that we can use to navigate back and forth among screens.

**Check code samples under master branch to get a better understanding on this.**

- **Push:** The push method is used to add another route onto the top of the current stack. The new page is displayed over the previous one.

      onPressed: (){  
	      Navigator.push(context, new MaterialPageRoute(  
			  builder: (context) => Page2()  
	      ));  
      }
    

- **Pop:** Since the Navigator works like a stack, it uses the LIFO (Last-In, First-Out) principle. The pop method removes the topmost route from the stack. This displays the previous page to the user.

      onPressed: (){  
	      Navigator.pop(context);
	  }
Everything seems okay but,

What if there's two buttons to navaigate back to the previous page (Something like android system back button) ?

This is why Flutter has given us **[WillPopScope widget](https://api.flutter.dev/flutter/widgets/WillPopScope-class.html)**

Do you wanna try out the code? then...

    $ git checkout simple_routing


#### 2.2 Named Routing

The only difference in **Named Routing** approach is, we declare the routes in the main.dart file using routes () to use in further sections related to flutter. Please find the



    class MyApp extends StatelessWidget {  
      // This widget is the root of your application.  
      @override  
      Widget build(BuildContext context) {  
        return MaterialApp(  
          title: 'Flutter Demo',  
          theme: ThemeData(  
            primarySwatch: Colors.blue,  
          ),
	  
      	 //Declaring routes 
         routes: <String, WidgetBuilder>{  
            '/page1': (BuildContext context) => new Page1(),  
            '/page2': (BuildContext context) => new Page2(),  
         },  
      
          home: Page1()  
        );  
      }  
    }

When we call the navigation related methods with our button action or any other user interaction this how we do it.

    onPressed: (){  
      Navigator.of(context).pushNamed('/page2');  
    }

Further more you can check the flutter dev guide related to the [Named Routing](https://flutter.dev/docs/cookbook/navigation/named-routes)


You can find the complete [video tutorial related to this topic in my YouTube channel (Dilum De Silva)](https://www.youtube.com/watch?v=PmNfNZ6QzOM&t=28s)

Don't forget to like the video and subscribe the video 😌😉 if you felt it's useful. 🤟
