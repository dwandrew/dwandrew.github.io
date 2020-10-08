---
layout: post
title:      "When JavaScript came to tea."
date:       2020-10-08 15:21:00 +0000
permalink:  when_javascript_came_to_tea
---


So my friends, join me on a journey. I shall take you back, back through the mists of time to three days ago. Where JavaScript classes were scary and foreign creatures, their purpose as clear as the Limpopo river to me (the muddy bits of it anyway).
Anyway, I’m gonna talk about JavaScript now. It’s project four time with Flatiron School, and having moved on from Ruby on Rails I have entered the fearsome lands of JS, where Semicolons once roamed wild across the plains.
For this project I wracked my brain, and having watched a lot of Avatar: The Last Airbender recently, I decided the only logical thing to do was design a Chimera Builder. That is an app that allows you to create a single composite creature out of other animals traits or allow behind the scenes randomisers to choose for you.
A screenshot of the chimera creation screen. Including select boxes for Head, Torso, Legs, Tail, Wings and Habitat
Chimera creation form, I must admit, the CSS looks a little rusty but i’m yet to sign off on it as finished.


Chimeras as displayed on the page
The wonderful thing about JavaScript is that it updates the page without the requirement for a reload. A very handy trait for doing things on singular pages.
For instance this very page on Medium I am writing on now will be running via javascript, with the input forms for images and the text boxes all being populated in real time, without me needing to load a new page every time I add an image or any text! Some kind of tech wizardry amirite.
JS is grand as it operates entirely in browser, and this is how I now get along to chatting about classes.
As I mentioned above, JavaScript classes usefulness has only recently dawned on me. Its all about keeping your code nice and DRY (dont-repeat-yourself) as well as aiding in separating your JS files into nice manageable segments. My original JS file (before transferring elements into classes) was 700 + lines of code. Using separate JS class files managed to drop the core JS file down to about 250!
All you need to do is make sure you are still adding the JS file via script on the html of the page and you are golden, all the different JS files will communicate as they are all running on the page at the same time!
A screenshot of the javascript files added into HTML
Make sure all the JS files are added, otherwise your code will run funky!
JavaScript Classes are very useful in the fact that unlike Ruby Classes, you can assign callable functions to them, these can either be Static (assigned to the class itself) or Instance level.
class CandyPeople{
    constructor (name, flavour){
          this.name = name;
          this.flavour = flavour;}
    static whoMadeThem(){
        return "Candy people were all made by Princess Bubblegum"}
}
In the above example Candypeople as a class will return“Candy people were all made by Princess Bubblegum” if CandyPeople.whoMadeThem() static function is called.
Instance functions will only work once the class has been instantiated, following the above example let’s add an instance function
class CandyPeople{
    constructor (name, flavour){
          this.name = name;
          this.flavour = flavour;}
static whoMadeThem(){
        return "Candy people were all made by Princess Bubblegum"}
lemongrabScream(){ 
        if(this.name ==="LemonGrab")
        {return "UNACCEPTABLE"}
        else {return "How can we help you Finn?"}
}
}
lemongrabScream is an instance function, which means it only works when the class is instantiated. I slapped together this in the console and used it to demonstrate both types of function.
A demonstration of static versus instance functions in JS.
Instance versus Static functions
A final example just to show that Static functions do not work on instances and visa versa
An example showing that Instance Functions don’t work on Classes and Static functions don’t work on instances

Using instance methods on a class is…
As you can see they are not even recognised as functions at the scope at which they are being asked. Very handy for dodging weird bugs and meaning your code only acts as you want it to!
You may well have noticed above in the lemongrabScream function as well as in the constructor for the class, that the keyword ‘this’ was used. You may indeed ask what’s this?
Jack Skellington from nightmare before Christmas asking ‘What’s this?’
Yes this took me longer to make than i would like to admit. I have no regrets.
So, ‘this’ is a great Keyword in Javascript. It returns the object at which level it is called. This as a sentence makes no sense until it suddenly does, something i hope to help with shortly.
Let’s make a new class to demo this shall we.
class HalloweenMonster{
    constructor (name, theme){
          this.name = name;
          this.theme = theme;}
static whatsThis() {return this}
theresSomethingInTheAir(){ return this}
}
As you can see above, I have now made a new class with one static function and one instance function. Now let’s answer “What’s this?”.
A section of code in the console examining what ‘this’ is at different levels
Examining this
So, as you can see I first create the class, then instantiate jack. Time now to call some functions!
Calling the static method will returns the Classes version of ‘this’, and as it is a method at the class level, it returns the class.
I call the instance function on jack, also returning the instances version of ‘this’. However now it returns the instance as the function is at the instance level!
Finally I call ‘this’ outside of the class entirely, now it returns the window in which it is being called as that is the level at which it is being requested.
Hopefully this makes sense to you all wonderful readers, as now it is returning where it is being called once again!
It is incredibly useful in the constructor method, as it allows assignment of attributes directly to the instance as it is being created.
This has lead me full circle back to why JS classes are hugely useful.
They are so useful as a means to can pass on a lot of the heavy lifting to the class itself, allowing errors to be spotted far more easily and to be able to follow the flow of code through your program far more easily. Putting everything in a nice neat little compartment to do the work for itself, rather than creating a terrifying labyrinth of code where following the maze drives one quite, quite mad (and let’s not forget about minotaurs).
If you want to try any of this in the console don’t hesitate to pop it open and copy my code over and give it a try!
I hope this makes sense to y’all and if you have any questions feel free to drop me a comment and I’ll do my best to answer any queries you all may have!
If any of you want to have a gander at any of my work so far, don’t hesitate to pop along to https://github.com/dwandrew
Dan

