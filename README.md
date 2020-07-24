# Backend-1-Week-6-Sinatra

Make a git branch called backend1-lesson-6.  When you have the program working and complete, push it to github and create a pull request as usual.

# Setting up for Sinatra

You will need to do  
  
gem install sinatra  
  
From the command line to install Sinatra.  When you run the Sinatra program, you will connect to it from your browser using the address 

localhost:4567 

UNLESS you are running vagrant.  For students running vagrant, you must start the program with the parameters

-p 3000 -o 0.0.0.0   

Then you use the address 

localhost:3000 

to connect to the
program from your browser.

# Sinatra exercise for week 6

This Sinatra project is a Web Guesser.  The program chooses a secret number at random from 1 to 100.  The user gets at most 7 guesses for the number.  For each guess, if the guess is more than 10 less than the secret number, the program says Your guess is much too low.  If the guess is within 10, but too low, the program says, your guess is close but too low.  If the guess is within 10, but too high, the program says, your guess is close but too high.  If the guess is more than 10 too high, the program says, your guess is way too high.  If the user guesses right, the program says you win, but if the user runs out of guesses, the program says you lose.  The screen shows the list of guesses.  If the user wins or loses, a screen is put up that announces the result, with a "play again" button at the bottom to restart the game.

You will need to create a sinatra program called web-guesser.rb plus two erb files.  The erb files will be in the views directory.

Optional: The screen should change color based on the closeness of the user's guess.  Be sure to use light colors so that the text can be read.

Please try out the program.  You run ruby web-guesser.rb and then go to your browser, where you enter the url localhost:4567 (except for people running vagrant -- see 
above).

# Sessions

A web server such as Sinatra is designed to service concurrent requests from many users.  You have to have a way of keeping the data for each of those user sessions,
and keeping it separate so that user 1 does not see user 2's data and conversely.  The way this is done in Sinatra as well as other web servers is to use a session.
The data is actually kept in a cookie that flows back and forth between the browser and the web server.  Near the top of your progam, you must put

enable :sessions

to turn sessions on in Sinatra.  This gives you access to the session variable, which is a hash, so you can store whatever values you want in it, each under 
a separate key, as follows:

```ruby
session[:secret]=57
session[:guess_history]=[11, 23]
```

# Some hints

You will need one erb file which will display the guesses so far.  It will also display how good the guess was, as described above.  Finally it will prompt the
user, using an entry field and a submit button, for the next guess.  

The second erb file is for the completion of the game.  It will display all the previous information, as well as whether the user won or lost,
and it will have a submit button that says "play again" to restart the game.

You will need two routes in your web-guesser.rb file.  For  

```ruby
get '/' do
# your code here
end
```
  
you would initialize the program with a random secret number from 1 to 100, which is what the user
is to guess.  You would also initialize an array where you will keep the user's history of guesses.  Then you put up the first erb file, that prompts the user for a guess.
When the user makes a guess, that will be a post, so you will have a second route in your Sinatra program:  
  
```ruby
post '/' do
# your code here
end
```
  
The code here will check the guess and and put the erb file back up again, with
appropriate feedback to the user included, unless the user has won or is out of guesses, in which case
it will put up the other erb file.  When the post is called, a parameter (the guess) is passed, as params[:guess].  You can pass information to the erb files by putting it
in instance variables, which start with the @ sign.


