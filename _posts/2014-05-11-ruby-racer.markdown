---
layout: post
title: "Ruby Racer"
comments: true
date: 2014-05-11 22:56:21 -0400
---

I've enrolled in Dev Bootcamp to help accelerate my learning. Week 1 was all about ruby algorithms. This involved converting roman numerals to Arabic, creating chess boards, boggle and building an app that solves sudoku. After week 1 at DBC you will never look at sudoku the same way again. I forgot to mention the different search methods (dictionary, linear, binary, etc.), nested arrays, regex drills, and good ol' ruby racer. Ruby racer was actually a lot of fun. And don't get me started on the 7 books we had to read. **spoiler alert**: POODR is the most important read (Practical Object-Oriented Design in Ruby)

## Ruby Racer

``` ruby
require_relative 'racer_utils'

class RubyRacer

  attr_reader :players, :length, :die

  def initialize(players, length = 30)
    @players = {players[0] => 0, players[1] => 0}
    @length = length
    @die = Die.new
  end

  # Returns +true+ if one of the players has reached
  # the finish line, +false+ otherwise
  def finished?
    players['a'] >= length || players['b'] >= length
  end

  # Returns the winner if there is one, +nil+ otherwise
  def winner
    return players.key(players['a']) if players['a'] >= length
    return players.key(players['b']) if players['b'] >= length
  end

  # Rolls the dice and advances +player+ accordingly
  def advance_player!(player)
    players[player] += die.roll
    players[player] = length if players[player] > length
  end

  # Prints the current game board
  # The board should have the same dimensions each time
  # and you should print over the previous board
  def print_board
    puts " | " * players['a'] + ' a ' + " | " * (length - players['a'])
    puts " | " * players['b'] + ' b ' + " | " * (length - players['b'])
  end
end

players = ['a', 'b']

game = RubyRacer.new(players)

# This clears the screen, so the fun can begin
clear_screen!

until game.finished?
  players.each do |player|
    # This moves the cursor back to the upper-left of the screen
    move_to_home!
  end
end

# The game is over, so we need to print the "winning" board
clear_screen!
move_to_home!
game.print_board

puts "Player '#{game.winner}' has won!"



```
## die.rb

``` ruby
class Die
  def initialize(sides = 6)
    @sides = sides
  end
  def roll
    1 + rand(@sides)
  end
end

# Use "reputs" to print over a previously printed line,
# assuming the cursor is positioned appropriately.
def reputs(str = '')
  puts "\e[0K" + str
end

# Clear the screen
def clear_screen!
  print "\e[2J"
end

# Moves cursor to the top left of the terminal
def move_to_home!
  print "\e[H"
end

# Flushes the STDOUT buffer.
# By default STDOUT is only flushed when it encounters a newline (\n) character
def flush!
  $stdout.flush
end

```
Week 2 consists of recursion, ARGV basics, benchmarking, OOD, TDD, team projects and SQL.

### Fibonacci example:
``` ruby
def is_fibonacci?(i, num0 = 0, num1 = 1)
    if i == num0 || i == num0 + num1
        return true
    elsif i < num1
        return false
    end
    is_fibonacci?(i, num1, num0 + num1)
end
```

week 3 is more SQL, OO, TDD. This is also the week they introduce ActiveRecord and Sinatra. Perhaps this doesn't sound like much... but believe me it is.

#### What now?
So Now that I begin again tomorrow, I have the opportunity to learn it all again! Onward and upward!
---
![Why doesn't this work?](http://memeblender.com/wp-content/uploads/2013/05/As-a-programmer.jpg)
