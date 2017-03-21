# katanajs
A JavaScript-based HTML templating engine similar to Razor.  It's simple and awesome!

# Usage
Katana's usage is simple.  It's a single function which takes three arguments: `katana(templateCode, model, targetElement)`.  That's it!  The Katana `templateCode` argument can be loaded from a script tag, jQuery AJAX call, or anything that can spit back Katana-formatted templates.

# Templating Syntax
Katana's syntax is similar to that of Microsoft's Razor for C# or Laravel's Blade for PHP.  Katana, however, focuses on JavaScript.  Here's a quick template to get started:

## katana-view.js
    <div>
      <h1>{{ title }}</h1>
      <p>{{ content }}</h1>
      @if (items.length)
        <div>Here's the item list:</div>
        <ul>
          @each (var item in items)
            <li>{{ item.name }} - {{ item.description }}</li>
          @end
        </ul>
      @end
      @else
        <p>Sorry, no items available.</p>
      @end
    </div>
    
## model.js
    // Assuming we pass Katana the following model:
    var model = {
      title: 'Katana Demo',
      content: 'Katana is easy to use!  This text was dynamically generated using Katana!',
      items: ['HTML', 'JavaScript', 'Cascading Style Sheets', 'Katana']
    }

Much like the aformentioned templating engines, Katana uses the `@` symbol to drop into native code.  Katana restricts that the `@` symbol must be the first non-whitespace character in order to enable JavaScript.  Currently, `@` will always drop into a statement block.  All statments can then be termniated with `@end`. The statements `@for`, `@if`, `@with`, `@while`, `@else` are currently supported.  Additionally, Katana adds `@each` which works like a C# or Java `foreach` loop, allowing direct access to an array or array-like object's elements.

Katana also uses the double brace notation `{{ variableName }}` to emit parts of the `model`.  Katana can access down a model's members or into arrays.  It can also call member functions with the brace syntax if necessary.
