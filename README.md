ctrl + shift + m

#### Basics
Save file with .rb
Open the Ruby command line
```Ruby
irb
```
Print a string
```Ruby
puts “Hello world!”
```
Print a string with a  variable
```Ruby
name = "Julie"
puts "Hello #{name}!"
```

#### Variable interpolation
Difference of using single quotes and double quotes. Single quotes will not interpret variables, double quotes will. Same with using %q(Hello #{name!}!) – this will not interpolate the variable, but %Q(Hello #{name!}!) will.
Q thing is not used very often.

#### Heredoc
Print strings on multiple lines. Here STRING can be anything.
```Ruby
string = <<-STRING
Hello
My name is Julie
Treehouse is fun!
STRING
puts string
```

#### Special characters
* \n – new line
* \t – tab
* \s - space

#### Prompts
```Ruby
puts "What is your name? "
name = gets.chomp
puts "Hi #{name}. Nice to meet you"
```
Adding the chomp onto gets removes the automatic line break. So when you print the last line the Nice to meet you doesn't go onto a new line.

#### String manipulation
* name.upcase – uppercase the string
* name.downcase – downcase the string
* name.reverse – reverse the characters in a string
* name.length - returns the length of the string (not a manipulator)

Can be chained on like this: name.reverse.downcase.upcase <br>
Each of these returns a new string, like a copy. It does not change the variable. <br>
Alternatively, If a method ends in an exclamation point it will change the variable.
* name.upcase! – changes the variable name to be uppercased

#### Classes
Ask ruby what type of thing a variable is:
```Ruby
a = 1
b = 2.2
c = “Julie”
a.class will return Fixnum
b.class will return Float
c.class will return String
```

#### List of Operators
* Multiplication: *
* Division: /
* Modulus, remainder: %
* Exponent: **

#### Methods
```Ruby
def add
    puts 2 + 2
end
add
```
Methods can take arguments – the number of arguments is called Arity

#### Example Method
```Ruby
def questionnaire
    puts "What is your name? "
    name = gets.chomp
    puts "\nHi #{name.capitalize}. How old are you? "
    age = gets.chomp
    puts "\nThat's a great age. What's your favorite movie? "
    movie = gets.chomp
    puts "\nOK great. So you are #{name}. And you are #{age} years old. And your favorite movie is #{movie}. Nice to meet you! I'm Ruby."
end
questionnaire
```

#### Comments
Use pound symbol (#) to write comments in Ruby

#### Comparison Operators
Equality / Inequality Operators - double equals in Ruby
```Ruby
a = 10
b = 11
a == b
    # returns false

name = "Julie"
name != "julie"
    # returns true

"a" > "A"
    # returns true because of the ASCII codes: "a".ord = 97, and "A".ord = 65
```

#### Control Structures
Branching - do something if a statement is true.
```Ruby
print "Enter name: "
name = gets.chomp
if name == "Julie"
    puts "That's my name, too!"
else
    puts "Hi #{name}!"
end
```

Using case instead
``` Ruby
print "Enter name: "
name = gets.chomp
case name
    when "Julie"
        puts "That's ny name, too!"
    else
        puts "Hi #{name}!"
end
```

#### Logical Operators
Turn a string into a number
```Ruby
print "What is your favorite number? "
number = gets.chomp.to_i
```

Not Operator. "If not car1 speed and car2 speed"
```Ruby
car1_speed = 50
car2_speed = 60

if !(car1_speed == car2_speed)
    puts "Car 1 and car 2 are not going the same speed."
end
```


#### Arrays
```Ruby
grocery_list = Array.new
    # Returns []
    # OR
grocery_list = []

# Add string interpolation
item = "milk"
grocery_list = %W(#{item} eggs bread)
puts grocery_list
puts grocery_list.inspect
    # This will print the actual array with the brackets and quotes
```

Add items to the Array
```Ruby
grocery_list = ["milk", "eggs", "bread"]
# Use << to add to an array
grocery_list << "carrots"
# Or use += to add to an array
grocery_list += ["ice cream", "pie"]
# Use unshift to add to the beginning of an array
grocery_list.unshift("celery")
# Or use push to add to an array
puts grocery_list.push("potatoes")
```

Array methods
```Ruby
grocery_list.at(1)
# returns grocery list item at index 1
grocery_list.first
# returns first item
grocery_list.last
# returns last item in the array
grocery_list[-1]
# another way to access the last item in the array
grocery_list.insert(2, "oatmeal")
# Insert oatmeal into the array at index 2
grocery_list.count
# Length of the array
grocery_list.count("eggs")
# Returns how many times eggs is in the array
grocery_list.include?("eggs")
# Does the array have eggs in it?
grocery_list.pop
# Remove the last item from the array
grocery_list.shift
# Remove the first item from the array
grocery_list.unshift("milk")
# Add an item to the beginning of the array
grocery_list.slice(0, 3)
# Remove 3 items, start index is the first number, second number is number of items to remove
grocery_list.drop(2)
# Remove last 2 items from the array
```


#### Hashes
```Ruby
item = {
    "name" => "Bread",
    "quantity" => 1
}
item["name"]
# Will return "Bread"
item.delete("quantity")
# Will delete hash key quantity
```

Working with keys inside a Hash
```Ruby
hash = {
    "item" => "Bread",
    "brand" => "Atlanta Bread Company",
    "quantity" => 1
}
hash.has_key?("brand")
# will return true
hash.store("calories", 300)
# Add a new hash key
```

Methods for working with Hash values
```Ruby
hash.values
# return an array with all of the values inside the hash
hash.has_value?("Bread")
# will return true because "Bread" is a value
hash.values_at("item", "quantity")
# Returns an array of values for the keys that were passed in
```
Print hash keys and values. Use [items].each do |item|. And item becomes each hash pair and you can access the values.
```Ruby
def print_list(list)
    puts "List: #{list['name']}"
    puts "-------"
    list["items"].each do |item|
        puts "Item: " + item['name']
        puts "Quantity: " + item['quantity'].to_s
        puts "-------"
    end
end
```

#### Loops
Do loop
```Ruby
loop do
    print "Do you want to continue? (y/n) "
    answer = gets.chomp.downcase
    if answer == "n"
        print "Bye!"
        break
    end
end
```

While loop
```Ruby
array = [0, 1, 2, 3, 4, 5]
i = 0
while i < array.length
    item = array[i]
    puts "The current item is #{item}."
    i += 1
end
```

Until loop
```Ruby
answer = ""
until answer == "n"
    print "Do you want this loop to continue? (y/n) "
    answer = gets.chomp
end
```

Times loop
```Ruby
5.times do |i|
    if i == 2
        puts "Hola!"
    else
        puts "Hello!"
    end
end
```

For loop
```Ruby
for item in 1..10 do
    puts "The current item is #{item}."
end
```


#### Each Method
This is apparently the most common way Ruby programmers write loops. They do not use the for loop very often.
```Ruby
array = [0, 1, 2, 3, 4, 5]
array.each do |item|
    item = item + 2
    puts "The current item + 2 is #{item}."
end
```

#### Using iteration on hashes
``` Ruby
business = {
    "name" => "Chick Fil A",
    "location" => "Atlanta, GA"
}
business.each do |key, value|
    puts "The hash key is #{key} and the value is #{value}."
end
```

#### Objects
Everything in Ruby is an object. You can call methods on objects.

#### Classes
``` Ruby
class Name
    class Name
        # Attribute reader method - ruby creates a method which returns the variable.
        attr_reader :title, :first_name, :middle_name, :last_name
        def initialize(title, first_name, middle_name, last_name)
            # instance variable will be available to each method in the class
            @title = title
            @first_name = first_name
            @middle_name = middle_name
            @last_name = last_name
        end
    end

    name = Name.new("Ms.", "Julie", "Marie", "Dyer")
    puts name.title + " " + name.first_name + " " + name.middle_name + " " + name.last_name
```

to_s method
Use this to set a name for the object. This is what will be returned when you try to print just the class without any methods on it.
``` Ruby
def to_s
    name_with_title
end
```


#### Boolean precedence
Order in which boolean statements are evaluated matters.
```Ruby
1 && 2 == 1 && 2
# this returns false, because Ruby interprets this as:
1 && (2 == 1) && 2
# to correct this you need to write it like this, because parenthesis has higher precedence
(1 && 2) == (1 && 2)
# now this will return true
```

#### Conditional Assignment
Want to define a variable but the variable may or may not exist.
``` Ruby
name = "Julie"
if defined?(name)
    name
else
    name = "Andrew"
end

# This is the same as. Andrew will only be assigned if the variable name does not exist.
name = "Julie"
name ||= "Andrew"
```


#### Blocks
Implict return in blocks:
```Ruby
arr = [1, 2, 232, 234, 23, 1]
arr.length.times do |i|
    puts "Hello world!"
    puts i
    # implicit return - this returns the last item of the block, don't use the return keyword
    true
end
```

Running statements within blocks. If you call yield without a block you will get an error.
```Ruby
def block_method
    puts "This is the first line in block_method"
    # Tells ruby to execute the code in the block
    yield
end

block_method do
    # This is the block
    puts "This statement is called from the block."
end
```

Kind of like callbacks in JavaScript
```Ruby
def get_name
    print "Enter your name: "
    name = gets.chomp
    yield name
    # implicit return of the name variable
    name
end
# My name now gets assigned to name, because name is returned from calling get_name
my_name = get_name do |name|
    puts "That's a cool name, #{name}!"
end
```

Another way to write blocks
```Ruby
def get_name(prompt, &block)
    print prompt + ": "
    name = gets.chomp
    block.call(name)
    # implicit return of the name variable
    name
end

# My name now gets assigned to name, because name is returned from calling get_name
my_name = get_name("Enter your name") do |name|
    puts "That's a cool name, #{name}!"
end
```

#### Blocks like higher order functions
These work with hashes as well, just instead of passing in one item you pass in key, value. <br>
map - returns a new array with the block executed over each item in the array
```Ruby
arr = [1, 2, 3, 4, 5, 6, 7]
mapped = arr.map do |item|
    item * 2
end
puts mapped
```

reject - returns only items which pass the condition in the block
```Ruby
arr = [1, 2, 3, 4, 5, 6, 7]
odds = arr.reject do |item|
    item % 2 == 0
end
puts odds
```

select - returns a new array containing all items which return true from the block
```Ruby
arr = [1, 2, 3, 4, 5, 6, 7]
even = arr.select do |num|
    num % 2 == 0
end
puts even.inspect
```
