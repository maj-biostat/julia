# Introductory Julia

## Remarks

[neovim](neovim.md) and [tmux](multiplexer.md) contain some useful environment setup notes. 

Clear the repl.  

```
julia> ;
shell> clear
```

To compile a file:

```
terminal$ julia file.jl
```

The following is mainly a condensed summary of a youtube tutorial [Julia Tutorial](https://www.youtube.com/watch?v=sE67bP2PnOo)

## Variables (hello world)

Types are dynamically assigned and are mutable (int to string).

```
# Bring in modules
using Printf
using Statistics

# Declare a variable and then update it - no problemo
s = 0
s = "Dog"
println(s)
```

However, note that you can assert different data types if you really want to.

## Data types

Basic types:

+ booleans (true or false)
+ various Int8, 16 etc, BigInts, the latter giving you increased precision.
+ various Float32, Float64, BigFloat
+ characters (text surrounded by single quote) 

## Casting

```
# From float to unsigned int.
i1 = UInt8(trunc(3.14))
println(i1)
# From string to float
f1 = parse(Float64, "22.9")
# barfs
i2 = parse(Int8, "22.9") 
# ok
i2 = parse(Int8, "22") 
```

## Strings

```
s1 = "Random string surrounded by double quote"
# Note use """blah blah ... """ if you have multiline strings to declare.
println(length(s1))
println(s1[1])
println(s1[end])
println(s1[1:4])
s2 = string("A", "Test")
println(s2)
println("A " * "Concatenation")
i3 = 2
i4 = 3
println("$i3 + $i4 = $(i3 + i4)")
# find index
println(findfirst(isequal('i'), "Trick"))
println(occursin("key", "monkey"))
```
## Conditional

```
# && || ! (and or not)
if x > 12 && y < 10
  println("hit it")
elseif age < 12
  println("wha")
else 
  println("y")
end
```

Ternery operator:

```
# condition ? "if true" : "if false"
true || false ? "true" : "false"
```

## Loop

```
i = 1
while i < 20
  if (i%2) == 0
    println(i)
    # access global outside loop
    global i += 1
    continue
  end
  global i += 1
  if i >= 10
    break
  end
end
```

```
for i = 1:5
  println(i)
end
for i in [2, 3, 5]
  println(i)
end
# j with a step
for i = 1:5, j = 2:2:10
  println((i, j))
end
```

## Array

```
# 2x2 array of int32
a1 = zeros(Int32, 2, 2)
a2 = Array{Int32}(undef, 5)
a3 = Float64[]
a4 = [1,2,3]
println(5 in a4)
# generic to use in findall
f(a) = (a >= 2) ? true : false
println(findall(f, a4))
# Count occurrences of
println(count(f, a4))

# Size, dim etc
println(size(a4))
println(length(a4))
println(sum(a4))
# Weird - Introduce 8 and 9 starting at index 2 in a4
splice!(a4, 2:1, [8,9])
println(a4)
# Now remove them
splice!(a4, 2:3)
println(maximum(a4))
println(minimum(a4))
# vector op
println(a4 * 2)
```

## Tuple

## Dict

## Set

## Functions

## Anon functions

## Math

## Enum

## Symbols

## Struct

## Abstract type

## Exception

## File IO

## Macro



