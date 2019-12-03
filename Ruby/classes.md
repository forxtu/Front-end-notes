## Classes and Objects

```ruby
class Book
  attr_accessor :title, :author

  def readBook()
    puts "Reading #{self.title} by #{self.author}"
  end
end

book1 = Book.new()
book1.title = "Harry Potter"
book1.author = "JK Rowling"

book1.readBook()
puts book1.title
```

## Constructors
```ruby
class Book
  attr_accessor :title, :author
  def initialize(title, author)
    @title = title
    @author = author
  end

  def readBook()
    puts "Reading #{self.title} by #{@author}"
  end
end

book1 = Book.new("Harry Potter", "JK Rowling")
# book1.title = "Half-Blood Prince"

puts book1.title
```

## Getters and Setters
```ruby
class Book
  attr_accessor :title, :author
  def initialize(title, author)
    self.title = title
    @author = author
  end

  # set
  def title=(title)
    puts "Set"
    @title = title
  end

  # get
  def title
    puts "Get"
    return @title
  end
end

book1 = Book.new("Harry Potter", "JK Rowling")

puts book1.title
```

## Inheritance
```ruby
class Chef
  attr_accessor :name, :age
  def initialize(name, age)
    @name = name
    @age = age
  end

  def make_chicken()
    puts "The chef makes chicken"
  end

  def make_salad()
    puts "The chef makes salad"
  end

  def make_special_dish()
    puts "The chef makes a special dish"
  end
end

# < means extends
class ItalianChef < Chef
  attr_accessor :country_of_origin
  def initialize(name, age, country_of_origin)
    @country_of_origin = country_of_origin
    super(name, age)
  end

  def make_pasta()
    puts "The chef makes pasta"
  end

  def make_special_dish()
    puts "The chef makes chicken parm"
  end
end

my_chef = Chef.new()
my_chef.make_chicken()

my_italian_chef = ItalianChef.new()
my_italian_chef.make_chicken()
```