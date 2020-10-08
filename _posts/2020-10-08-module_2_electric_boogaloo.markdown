---
layout: post
title:      "Module 2: Electric Boogaloo"
date:       2020-10-08 15:17:23 +0000
permalink:  module_2_electric_boogaloo
---

So here we are nearing the end of Module 2 of the Online Flatiron Software Engineering course. This module has been going from basic use of SQlite all the way up to using it within Sinatra to make a fully functioning database with constructed GUI.
So I, like the nerd I am, decided to expand on my original CLI project or the monster and spells manager to create a spellbook manager for users. This would allow a logged in user to create spellbooks and populate them with either the pre-populated catalogue of 5e spells Dnd 5e Spells list or create and design their own spells via a custom editor.
These spells are kept in a separate listing for each logged on user, so one user cannot access another's private creations.

Each user can also access, edit and delete all their own created spells alongside their spellbooks. However they cannot do the same to any others materials. This was done by the use of Session Cookies and a combination of helper methods and hard coding.

Comparing an items user_id to the session_id allowed for prevention of one user gaining access to a different users materials.
I ran into trouble early on where each individual spell could only belong to a single book, and should another book use that spell, it would then be removed from the first. This I rectified with the creation of the join table and allowing for the manufacture of the many to many relationship I required.

Using the sinatra-flash gem was very useful in allowing error messages to pop up within the program in a more useful format to it just crashing. All in all i used them rather gratuitously, but better that not!
All in all, I am rather content with the build on this so far, and look forward to improving it further with a good purge or redundant code as well as some refactoring whilst I go.

To achieve all this I had to learn a whole heap of new skills going all the way from 'what on earth is a rakefile and how can it help me' to database management, migration and seeding!
Fortunately I managed to scavenge my seed data from my previously built CLI project and use the same API scraper with a few minor adjustments to allow it to populate a database.
Previous to this, Ihad to make the tables to populate using active record, the corneal gem made this really easy as it allow very quick creation of schema tables like the one below
I think all in all from the creation of the whole project my favourite aspect may well be the very simple dropdown buttons, using a mesh of javascript and css. When when naming the div's you just have to use collapsible for the main button! Incredibly handy way of reducing the impact of large chunks of text on your page!

Anyway, thats my two cents on the latest project. If anyone has any ideas for improvements or mods please feel free to comment below! I have considered adding a Monsters section to this as well, allowing people to make easily tracked monster groups! Could be especially useful for monster spellcasters as I can include collapsible spell buttons for them! What do you all think?
Peace out and Nerd on folks!
Dan

The content of your blog post goes here.
