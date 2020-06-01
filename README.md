# Backend-1-Week-6-Sinatra
Sinatra exercise for week 6

This Sinatra project is a Web Guesser.  The program chooses a secret number at random from 1 to 100.  The user gets at most 7 guesses for the number.  For each guess, if the guess is more than 10 less than the secret number, the program says Your guess is much too low.  If the guess is within 10, but too low, the program says, your guess is close but too low.  If the guess is within 10, but too high, the program says, your guess is close but too high.  If the guess is more than 10 too high, the program says, your guess is way too high.  If the user guesses right, the program says you win, but if the user runs out of guesses, the program says you lose.  The screen shows the list of guesses.  If the user wins or loses, a radio button allows them to select whether to play again, in which case a new secret number is chosen.

The user's guess is collected in a number field, and there is a submit button on each screen.  The random number and the history of user guesses is kept in the session hash.

You will need the sinatra program web-guesser.rb plus two erb files.

Optional: The screen should change color based on the closeness of the user's guess.  Be sure to use light colors so that the text can be read.
