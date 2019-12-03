## Printing
```ruby
puts "Hello"
print "World"
puts "!"
```

## Variables and Data Types
```ruby
=begin
 Names are case-sensitive and may begin with:
     letters, _
 After, may include
     letters, numbers, _
 Convention says
     Start with a lowercase word, then additional words are lowercase separated
     by an underscore
     ex. my_first_variable
=end
name = "Mike"     # Strings
age = 30          # Integer
gpa = 3.5         # Decimal
is_tall = true    # Boolean -> True/False

name = "John"

puts "Your name is #{name}"
puts "Your name is " + name

```

## Casting and Converting

```ruby
puts  3.14.to_i
puts  3.to_f
puts "3.0".to_s

puts 100 + "50".to_i
puts  100 + "50.99".to_f
```

## Strings
```ruby
greeting = "Hello"
#indexes:   01234
puts greeting.length
puts greeting[0]
puts greeting.include? "llo"
puts greeting.include? "z"
puts greeting[1,3]
```

## Numbers
```ruby
puts  2 * 3         # Basic Arithmetic: +, -, /, *
puts  2**3          # Exponent
puts  10 % 3        # Modulus Op. : returns remainder of 10/3
puts  1 + 2 * 3     # order of operations
puts 10 / 3.0       # int's and doubles


num = 10
num += 100          # +=, -=, /=, *=
puts num

num = -36.8
puts  num.abs()
puts  num.round()

# Math class has useful math methods
puts Math.sqrt(144)
puts Math.log(0)
```

## User input
```ruby
puts "Enter your name: "
name = gets                             #.chomp
puts "Hello #{name}, how are you"

puts "Enter first num: "
num1 = gets.chomp
puts "enter second num: "
num2 = gets.chomp
puts num1.to_f + num2.to_f
```

## Methonds
```ruby
def add_numbers(num1, num2=99)
  return num1 + num2
end

sum = add_numbers(4, 3)
puts sum
```

## If Statements
```ruby
is_student = false
is_smart = false

if is_student and is_smart
	puts "You are a student"
elsif is_student and !is_smart
	puts "You are not a smart student"
else
	puts "You are not a student and not smart"
end

# >, <, >=, <=, !=, ==, String.equals()
if 1 > 3
	puts "number comparison was true"
end

if "a" > "b"
  puts "string comparison was true"
end
```

## Switch Statements
```ruby
my_grade = "A"
case my_grade
  when "A"
    puts "You Pass"
  when "F"
    puts "You fail"
  else
    puts "Invalid grade"
end
```

## While Loops
```ruby
index = 1
while index <= 5
	puts index
	index += 1
end
```

## For Loops
```ruby
# 1
for index in 0..5
  puts index
end

# 2
5.times do |index|
  puts index
end

# 3
lucky_nums = [4, 8, 15, 16, 23, 42]
for lucky_num in lucky_nums
  puts lucky_num
end

# 4
lucky_nums.each do |lucky_num|
  puts lucky_num
end
```

## Exception Catching
```ruby
begin
  # puts bad_variable
  num = 10/0
rescue ZeroDivisionError
  puts "Error"
rescue
  puts "All other errors"
end

raise "Made Up Exception"
```