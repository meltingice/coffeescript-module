# coffeescript-module

A base class for your Coffeescript projects.

## Examples

``` coffeescript
{Module} = require 'coffeescript-module'

class Foo extends Module
  log: -> console.log 'hi!'

class Bar extends Module
  @delegate 'log', Foo
  @aliasFunction 'b', 'a'
  @aliasProperty 'd', 'c'

  c: 'test'
  a: -> console.log 'a'

class Baz extends Module
  @includes Bar

bar = new Bar()
bar.log() # calls Foo::log()
bar.b()   # calls Bar::a()
bar.d     # gets Bar::c

baz = new Baz()
baz.b()   # calls Bar::a()
```