---
layout: post
title: Swift之枚举
description: "Swift之枚举"
tags: [Swift post]
image:
  background: triangular.png
---

### Enumeration 语法

~~~ ruby
enum SomeEnumeration {
	// enumeration definition
}
~~~

例如，指南针枚举：

~~~ ruby
enum CompassPoint {
    case north
    case south
    case east
    case west
}
~~~

单行用","分隔：

~~~ ruby
enum Planet {
    case mercury, venus, earth, mars, jupiter, saturn, uranus, neptune
}
~~~

Each enumeration definition defines a brand new type. Like other types in Swift, their names (such as CompassPoint and Planet) should start with a capital letter. Give enumeration types singular rather than plural names, so that they read as self-evident:

~~~ ruby
var directionToHead = CompassPoint.west
~~~

The type of directionToHead is inferred when it is initialized with one of the possible values of CompassPoint. Once directionToHead is declared as a CompassPoint, you can set it to a different CompassPoint value using a shorter dot syntax:

~~~ ruby
directionToHead = .east
~~~

The type of directionToHead is already known, and so you can drop the type when setting its value. This makes for highly readable code when working with explicitly-typed enumeration values.

### Associated Values

