Taggart allows you to tag Strings with HTML
===========================================
How and what
------------
```ruby
        "Hello World!".h1
```
returns
```
        <h1>Hello World!</h1>
```
or try (in bad typographical taste) 
```ruby
        "Important!".em.strong
```
to get 
```html
        <em><strong>Important!</em></strong>
```
or do some more nesting 
```ruby
        ("Label".td + "Value".td).tr.table
```
to render a small table
```html
        <table><tr><td>Label</td><td>Value</td></tr></table>
```
. Add HTML attributes as Ruby parameters.

```ruby
        "hello".span(class: 'stuff', id: 'thing')
```
to get a nice HTML string like this
```html
        <span class=\"stuff\" id=\"thing\">hello</span>
```
. You can also use arrays, how about this table?
```ruby
        (%w(r1c1 r1c2 r1c3).td.tr + %w(r2c1 r2c2 r2c3).td.tr).table
```
will produce this HTML (author's line breaks and indentation)
```html
        <table>
          <tr>
            <td>r1c1</td>
            <td>r1c2</td>
            <td>r1c3</td>
          </tr>
          <tr>
            <td>r2c1</td>
            <td>r2c2</td>
            <td>r2c3</td>
          </tr>
        </table>
```
. Naturally we can do single tags too.
```ruby
        "Gimme a".br
```
will return.
```html
        "Gimme a<br />" 
```

See the `spec/taggart_spec.rb` for more examples (until I have time to do a bigger-better-faster-example file).

Background:
-----------
I have a lot of Ruby code that marks some String in an HTML tag, usually with a 
specific CSS class. Or perhaps a link or so.
It's not particularly nice to write ```"<strong>#{my_variable}</strong>"```. The more 
complex the Ruby code is, the worse it is to have ```"```, ```#```, ```{``` or ```}``` soiling the code.
I was looking at the code and I thought, wouldn't it be nice if I could just tell that piece
of String that it's supposed to be a ```<span>``` or some other tag. One could simply 
write ```my_variable.strong``` to get the job done. **Taggart** was born.

The Idea
--------
The idea was to simplify the code and make it easier and faster for me to add arbitrary HTML into my
non-HTML code. I wanted to stop breaking my fingers trying to get the quote-string-hash-curlybrackets-code-curlybrackets-morestrings-quote
right on my keyboard.
It was _never_ intended to be a full-fledged HTML page renderer. If you want to use it for that, I'd love to see the result, though.


Installation:
-------------
Install the gem:
  ```gem install taggart```
Then load Taggart with:
  ```require 'taggart'```
Taggart is now active, which means you can play around.


History
-------
- Converted the README to markdown for a bit better formatting fun
- Added href and img feature.
- Created Gem
- Pushed code to Git.
- Created test Gem.
- Added files to create Gem and reorganised the file structure.
- Made dual_sub pass all the tests, and added the examples from .tr (translate) Ruby docs to the test.
- More work on the "dynamic namespace clash resolver", in other words, tr and sub work in both classic and Taggart way.
- Initial version of "dynamic namespace clash resolver" to fix issues with .tr
- Added basic RSpec test.
- Added namespacing for Strings and Arrays
- Implemented arrays; ["Label", "Value"].td.tr.table and ["First", "Second", "Third"].li.ol
- Tidied up things a bit.
- Added a version of attributes ("Red".span(class: 'red'))
- First version. Basic tags.


Future???
---------
With your blessing. Like Ozzy said; _"The crazier you get, the crazier Ozzy gets!"_, or something.

* Potential validations, could check file, size, etc
* Full fledged examples.
* Please send suggestions.


Issues:
-------
- ```"hello".sub('world', 'world')``` returns ```<sub  world  world>hello</sub>``` Not really perfect
- Please help me test it out.


Feedback welcome!!

Author: Jocke Selin <jocke@selincite.com>

Date: 2012-03-05

Version: 0.0.4 Build 009

Github: <https://github.com/jocke/taggart>