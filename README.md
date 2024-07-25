# Scala-Basics
Below is a detailed Markdown guide for Perl, covering the basics to intermediate topics:

---

# Perl Markdown Guide

## Introduction

Perl is a high-level, interpreted, and dynamic programming language. This guide will introduce you to the basics of Perl and move towards more intermediate topics. Let's get started!

## Table of Contents

1. [Getting Started](#getting-started)
    - [Installation](#installation)
    - [Hello World](#hello-world)
2. [Basic Syntax](#basic-syntax)
    - [Variables](#variables)
    - [Operators](#operators)
    - [Control Structures](#control-structures)
3. [Functions](#functions)
    - [Defining Functions](#defining-functions)
    - [Function Parameters](#function-parameters)
    - [Return Values](#return-values)
4. [Data Structures](#data-structures)
    - [Arrays](#arrays)
    - [Hashes](#hashes)
5. [File Handling](#file-handling)
    - [Reading Files](#reading-files)
    - [Writing Files](#writing-files)
6. [Regular Expressions](#regular-expressions)
7. [Modules and Packages](#modules-and-packages)
8. [Error Handling](#error-handling)
9. [Advanced Topics](#advanced-topics)
    - [References](#references)
    - [Object-Oriented Perl](#object-oriented-perl)
    - [Perl and the Web](#perl-and-the-web)

## Getting Started

### Installation

To install Perl, visit the [official Perl website](https://www.perl.org/get.html) and download the appropriate version for your operating system.

### Hello World

Create a file named `hello.pl` and add the following code:

```perl
#!/usr/bin/perl
use strict;
use warnings;

print "Hello, World!\n";
```

Run the script from the command line:

```sh
perl hello.pl
```

## Basic Syntax

### Variables

Perl has three main types of variables: scalars, arrays, and hashes.

#### Scalars

Scalars are single data items.

```perl
my $name = "John";
my $age = 30;
my $pi = 3.14159;
```

#### Arrays

Arrays hold ordered lists of scalars.

```perl
my @colors = ("red", "green", "blue");
print $colors[0];  # Outputs: red
```

#### Hashes

Hashes are sets of key/value pairs.

```perl
my %fruit_colors = (
    apple  => "red",
    banana => "yellow",
    grape  => "purple",
);
print $fruit_colors{'apple'};  # Outputs: red
```

### Operators

#### Arithmetic Operators

```perl
my $sum = 5 + 10;
my $difference = 10 - 5;
my $product = 5 * 10;
my $quotient = 10 / 5;
my $remainder = 10 % 3;
```

#### String Operators

```perl
my $string1 = "Hello";
my $string2 = "World";
my $concatenated = $string1 . " " . $string2;  # Outputs: Hello World
my $repeated = $string1 x 3;  # Outputs: HelloHelloHello
```

### Control Structures

#### If-Else

```perl
my $age = 18;

if ($age >= 18) {
    print "Adult\n";
} else {
    print "Minor\n";
}
```

#### Loops

##### For Loop

```perl
for (my $i = 0; $i < 10; $i++) {
    print "$i\n";
}
```

##### Foreach Loop

```perl
my @colors = ("red", "green", "blue");

foreach my $color (@colors) {
    print "$color\n";
}
```

##### While Loop

```perl
my $count = 0;

while ($count < 5) {
    print "$count\n";
    $count++;
}
```

## Functions

### Defining Functions

```perl
sub hello {
    print "Hello, World!\n";
}

hello();
```

### Function Parameters

```perl
sub greet {
    my ($name) = @_;
    print "Hello, $name!\n";
}

greet("Alice");
```

### Return Values

```perl
sub add {
    my ($a, $b) = @_;
    return $a + $b;
}

my $sum = add(2, 3);
print "$sum\n";  # Outputs: 5
```

## Data Structures

### Arrays

#### Push and Pop

```perl
my @stack;
push(@stack, "apple");
push(@stack, "banana");
my $fruit = pop(@stack);  # banana
```

#### Shift and Unshift

```perl
my @queue;
unshift(@queue, "apple");
unshift(@queue, "banana");
my $fruit = shift(@queue);  # banana
```

### Hashes

#### Adding and Removing Elements

```perl
my %hash;
$hash{'apple'} = 'red';
delete $hash{'apple'};
```

#### Iterating Over Hashes

```perl
my %fruit_colors = (
    apple  => "red",
    banana => "yellow",
    grape  => "purple",
);

while (my ($key, $value) = each %fruit_colors) {
    print "$key is $value\n";
}
```

## File Handling

### Reading Files

```perl
open(my $fh, '<', 'file.txt') or die "Cannot open file: $!";
while (my $line = <$fh>) {
    print $line;
}
close($fh);
```

### Writing Files

```perl
open(my $fh, '>', 'file.txt') or die "Cannot open file: $!";
print $fh "Hello, World!\n";
close($fh);
```

## Regular Expressions

```perl
my $string = "Hello, World!";
if ($string =~ /World/) {
    print "Match found!\n";
}
```

## Modules and Packages

### Using Modules

```perl
use strict;
use warnings;
use Data::Dumper;

my @array = (1, 2, 3);
print Dumper(\@array);
```

### Creating Modules

Create a file named `MyModule.pm`:

```perl
package MyModule;
use strict;
use warnings;
require Exporter;

our @ISA = qw(Exporter);
our @EXPORT = qw(hello);

sub hello {
    print "Hello from MyModule!\n";
}

1;  # End of MyModule
```

Use the module in a script:

```perl
use strict;
use warnings;
use MyModule;

hello();
```

## Error Handling

```perl
eval {
    die "An error occurred";
};
if ($@) {
    print "Error: $@\n";
}
```

## Advanced Topics

### References

```perl
my $scalar_ref = \$scalar;
my @array = (1, 2, 3);
my $array_ref = \@array;
my %hash = (key => 'value');
my $hash_ref = \%hash;

print $$scalar_ref;
print @$array_ref;
print %$hash_ref;
```

### Object-Oriented Perl

```perl
package Animal;
sub new {
    my $class = shift;
    my $self = {
        name => shift,
        sound => shift,
    };
    bless $self, $class;
    return $self;
}

sub speak {
    my $self = shift;
    print $self->{name} . " goes " . $self->{sound} . "\n";
}

package main;
my $dog = Animal->new("Dog", "Woof");
$dog->speak();
```

### Perl and the Web

#### CGI

```perl
use CGI qw(:standard);

print header;
print start_html('Hello CGI');
print h1('Hello, World!');
print end_html;
```

#### LWP::Simple

```perl
use LWP::Simple;

my $content = get("http://www.example.com");
print $content;
```

## Conclusion

This guide covers the basics and some intermediate topics in Perl. For more detailed information, refer to the [official Perl documentation](https://perldoc.perl.org/).
