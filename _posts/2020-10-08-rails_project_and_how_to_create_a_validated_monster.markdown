---
layout: post
title:      "Rails Project and How to Create a Validated Monster"
date:       2020-10-08 15:19:40 +0000
permalink:  rails_project_and_how_to_create_a_validated_monster
---



So here we are at the Rails Project stage, it feels like only yesterday I was doing simple addition programming and being wowed by it. Now I am making 11 model monsters with multiple has_many to has_many relationships.
What a lot can change in just a few months! I decided to take a different tack for this project and move away from Dungeons and Dragons, Instead I am now in the realm of designing a miniature game (a hybrid from two different rulesets I love). This is how we ask the question, how do you create a monster?

The answer is, little step by little step. It may seem like obvious advice but one thing I am really learning here is limiting the scope of what you are working on to one step at a time. First off create your basic Users access, sessions and single model relationship (in my case for the above app, its Users have warbands, warbands belong to a user)
From there add one layer at a time, I consecutively have now added warriors (which belong to warbands), then skills, equipment, armour etc. So the warriors can also be equipped and good at what they do!
Using validations and helper methods was important in allowing only those who are actually A. logged in, and B. actually the owners; edit and modify any of their own warbands and warriors.


A couple of my very useful helper methods
Use of the before_action: in the requisite controllers also helps keep the code lovely and clear of repeat code. This just means that you are free to make everything a lot more understandable to anyone else who is wanting to work on the project!

Using validations is a great way to make sure you are getting the data you need for your app to run smoothly as well, such as in my case, when a User is made the e-mail is not already in use, and the password meets the required complexity. Or Warbands have a name, and that name is at least 4 characters long when a new warband is created. This just saves your database just getting filled with useless dummy data.
Validations are run by rails before saving a new object, if any are invalid then it throws an error! Handy ey! It also allows the programmer to call the .valid? method to double check if an object has been made valid by rails or has failed validations, but more about that shortly.
To add validations you do so in the Model that you wish to validate and you have to specify the field you wish to validate (in the below case its the name field for Warband)

There are a great number of ways to validate some very handy and quite simple to use ones are as follows
Inclusion: Allows you to set specific parameters that the field has to match, it uses the option in: to allow you to add the required fields. With the %w turning the following brackets into a word array. Example provided below.
validates :type_of_mustelid, inclusion: { in: %w(ferret weasel stoat),

Length: Allows you to set a minimum/maximum/both length for the field.
validates :name_of_pet, length: { minimum: 2 }
validates :pet_description, length: { maximum: 500 }
validates :pets_age, length: { in: 1..5 }

Numericality: Will check if a field is given as a number, and it has a number of very useful options within it. Standardly it will convert anything entered into a float if it is a number, however you have the option :only_integer. To disallow any floats e.g it you were after a pets age and you didnt want to worry about a dog thats 4 & 3/4 years old!
validates :number_of_hamster, numericality: { only_integer: true }
A load of other options are provided such as
:even, must be even
:odd, must be odd
:greater_than, must be greater than
:greater_than_or_equal_to, must be greater than or equal to
:less_than, must be less_than
:less_than_or_equal_to, must be less than or equal to
:equal_to, must be equal
:other_than, must be anything but.

Presence: Checks that the field has been filled in with something other than nil or a blank string using the .empty? method. Usually important for making sure the fields that are really important are filled out
validates :pets_favourite_music, presence: true

Absence: Does the inverse of presence and makes sure that the field is left blank (either whitespace or nil) using the .present? method
validates :names_of_bad_dogs, absence: true
p.s they’re good dogs brent.
https://twitter.com/dog_rates/status/775410014383026176?lang=en

Uniqueness: checks to make sure that the entered field matches no other already saved version of that model (We can only have artist known as prince)
validates :artist, uniqueness: true

You can also use scope methods with the uniqueness trait to make sure that it does not cover ALL records, instead only those within the scope you are looking at.
A great thing about validations, is how they throw absolutely lovely error messages out for you! These can be accessed via Model_name.errors.messages 
which you can then allow to pop up on screen for the discerning user to be able to see what field they filled in wrong. Rather more useful than just the form repeatedly failing to submit because the User did not know that had to make sure their pet had a favourite song!

warband_alerts method setting any errors so they will be posted on the screen!
Anyways, I hope this made some sense to y’all and you have found it handy! Validations are a real handy tool to get you head around, but once you have they are quite simple really!
Feel free to suggest anything else that you would like me to go into a deep dive of, and I shall endeavour to make a blog post about it!
Dan

