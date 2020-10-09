---
layout: post
title:      "Dealing with Redux User Authentication & Flatirons Final Hurdle"
date:       2020-10-09 12:54:13 +0000
permalink:  dealing_with_redux_user_authentication_and_flatirons_final_hurdle
---


So my friends, here we are, I have prospered under the teachings of Flatiron up to this point and now I have reached the final grand Hurrah. My 5th (and final) Module is upon us dear readers.


The Aim of the final project is to create a single page React app, with Redux and a rails backend API to act as database.
I shall first pass you to this wonderful link, which aided my hugely in my initial setup : https://medium.com/swlh/react-reactions-cfdde7f08dff,

This will walk you through basic React setup allowing for user authentication. From here on out I am assuming the above article has been read and understood. If not, really do so, its great!
Today we are gonna talk about Redux and how to move on from where the above article takes you to fully getting User Auth up and running in Redux.

First let’s make sure we are in our client directory and head on into terminal and run.
npm install redux react-redux redux-thunk
This is going to install the important dependancies in your pack-lock.json and subsequently allow you to import those important bits that we are gonna need from here on out.
Head into your index.js file and now go ahead and import the following elements:



This will allow you to create a central store to retrieve information from at any level within your program (the big pro of Redux), and also allow you to make action creators that return a function instead of an action (the purpose of Thunk).
Now go ahead and add the following code

Right-o, if you have done that so far then you will have access to the store from within your App!
Now lets deal with signing up with redux first shall we, as you can’t very well sign in when there are no accounts to sign in with!
I have Structured the App I have been working with into a components, reducers and actions, and within them have separate files for each ‘area’ of the objectives I am dealing with, today we are only looking at user actions and authentication.
A layout of the file structure used in the demonstration App
File structure in my app
Lets head on into our Authentication components, and get our signup.js file open. The structure of this is going to be very similar to the structure given to you in the React demonstration, with a few key differences.
We are going to need to map dispatch to props, so we have access to some of our wonderful actions.
We are going to need to connect this file to the store so we can do no.1!
First let’s make sure we can connect to the store.


As you can see on line 2 we import { connect }, this allows us access to the wonderful central store.
Secondly on line 3 we are importing { createUser } from our actions folder, feel free to put that in now, but currently it won’d do anything as we have not made it yet!
Skip on down to the exporting of your component, we will need to do a couple of Modifications to make it all tickety-boo.


What on earth are we doing here you ask? Well, here is a good bit, Map dispatch to props is allowing us to access that wonderful createUser method that we have not made yet (don’t worry we will soon). Then adding connect to the export allows us access to the store with this component. We have to add null as the first argument in connect as usually this is mapStateToProps, but in this case we do not have to do that in this component.
Right then. We are nearly there. Now sharp eyed readers may have noticed in the first image we were calling:
this.props.createUser(this.state)
On line 22. This is using the now mapped createUser method from Props allowing us to access thunk actions! How very wonderful. Sounds to me like its times to head on over there and make the action we need!
First, if you are reading this and following along. Have a 2 minute break. Make yourself a cuppa, stretch your legs. This can all be a bit heavy.


Now you have had your break, on with the show!
Head on over to your actions folder and make a userActions.js file. This is where all our user actions are going to live and be imported from.


Within this action we are (as you can hopefully notice) sending a fetch request to our rails backend, using the path of ‘http://localhost:3001/users’ method ‘POST’ so it’s going to the create route in the users controller.
We create the strongParams from the passed in data (sent from our signup.js component) before sending this on back. If everything is present and correct with our sent data the user will be created and a JSON object will be sent back to us from the API end.
Now, what on earth are we doing with all this nonsense with:
dispatch({type: "CREATE_USER", user})
This my friends is using the dispatch action (provided by thunk), which will communicate with our reducer allowing us to add items to the global store! Neat eh?
Now time to sort out out reducer and we are on the home stretch!
First off lets make sure our root reducer is working out by adding our extra reducers:


As you can see here I have added a number of extra reducers, for the moment though we would only need the AuthReducer. This will allow use to add state to the store from within these reducers and to access is via the key we give in the combine reducers function. e.g any mapped state we make in AuthReducer will be accessible from the store via the key ‘auth’
Lets now go into our AuthReducer and have a look:


From this you can determine 2 things:
We are creating an initial state to be mapped to store
We are returning a modified state depending on what action.type is passed in.
Here we use a case statement to allow for many different types to be passed in (and therefore many different actions to do different things).
In our createUser information we want 2 things. Firstly once a user has created a profile the are ‘logged in’ and secondly that we can access some user information from the front end.
This is what we are doing in the return statement, as all this information can be accessed now from the frontend via store! Huzzah!
From here a state can be accessed via the store (using mapStateToProps) whereby once a user has been created they will remain logged in until the page is refreshed.
So sounds like we need a logout button as well. Have a quick think about how we would do such a thing. If you have been coding along why not give it a go. Then if you hit any real snags you can then view the solution below
If your thought was to create a clickable button that would access a mapped dispatch action to change the ‘logged_in’ status you are bang to rights.


All you would need to go to add this button is map it to props like we did with create user and call it with a logout button! (or however you so choose!)
Have another break now if you need it, for next we go onto logging in!
Image for post
So then my fine chums, we have before us a stored logged in status that can be accessed via state, and we can do so when we create a user….
Time for us to use some of that data that we have created. Time to try and Sign in.
Luckily this is very similar to our createUser method, however instead to sending to create, we are sending to our sessions controller !


The path ‘/login’ has been mapped in the previously mentioned setup article, so this will take use straight to the place we need!


Our reducer will then be actioned setting our ‘logged_in’ value to true if all the sign in data that was send to the backend was correct! From our SignIn.js


Finally we just need to make sure its app imported into our signIn component


We made it people! You should now have functioning Redux Sign In, Sign Out and create user functionality! Go forth now and prosper!
If you have any questions at all, please feel free to comment below, if you want to have a look at the github repo for this feel free to have a gander! Good Luck people and I hope this has been helpful.
Dan
Github repo:https://github.com/dwandrew/Thousand-Year-Chronicler
