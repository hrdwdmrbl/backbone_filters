_Disclaimer: This fork has been updated to work with Backbone 0.9.10_

# Usage

Include `backbone_filters.js` after Backbone.

In your router where routes are defined as:

```javascript
routes : {
    "clerks/:arg1/:arg2" : "clerks"
}

clerks : function(arg1, arg2) {
    // router logic, with arg1 and arg2
},
```

You can now add:

```javascript
before : {
  '^clerks' : function(route, arg1, arg2) {
    /* do stuff to all routes starting with 'clerks' */
    /* return false to halt execution */
  },
  'another reg ex' : function(route) { }
},

after : {
  '^clerks' : function(route, arg1, arg2) {
    /* do stuff */
  },
  'another reg ex' : function(route) { }
}
```

Your filters will be called and if a filter returns false, the filter chain is halted.
If a before filter chain is halted, the action in the Router will not be called.

Your filters will receive the same arguments that get passed to the actions (following the first argument, route). The route argument contains the entire matched filter segment (including args).