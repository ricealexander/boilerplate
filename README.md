# opinionated_reset
This will be an opinionated CSS reset.
Browser Support: all CSS should be supported on IE10+ and on all modern browsers

#### CSS Philosophy
1. Every property must give value
   All properties assigned to an element should be used. In, [Eric Meyer's CSS Reset](https://meyerweb.com/eric/tools/css/reset/index.html), `border: 0;` is applied to a number of tags that won't naturally contain a border, such as `html, body, div, span, ...`
   Although this keeps Meyer's stylesheet concise, those styles are wasted.

2. Reset properties should not need to be overridden
   One criticism of reset stylesheets is that they override default styles and in many cases are then overridden themselves. A common reset is to set the margin and padding of all elements to zero: `* {margin: 0; padding: 0;}`.
   This approach can be problematic with buttons and form elements, and if it's followed with new defaults for paragraph tags or headers, then the reset styles have undermined themselves.

3. Reset utilities are allowed for optional resets
   Some elements are frequently, but not always reset. One common example is the `ul` element. Unordered lists are often reset for semantic reasons, but although one might frequently have to reset it to `ul { margin: 0; padding: 0; list-style-type: none; }`, the default styles can be useful when you need a bulletted list.
   For elements like these, we can implement a reset class: `ul.reset`. 


#### Taking this a step further
4. Strictly avoid the universal selector `*`
   It's 2018, so negative performance implications of the universal selector are negligible. The issue with the universal selector is that it breaks rules 1 and 2. Properties added for specific reasons may be assigned to elements that don't need those properties, and global properties almost necessitate that they will be overriden for some elements.
   A common global style is the `* { box-sizing: border-box; }`. This rule serves to prevent any layout issues resulting from a set width when combined with padding and borders. Since most elements won't combine a set width with padding and borders, this box-sizing property is wasted on most elements that use it.

5. Strictly avoid `!important`
   This doesn't seem to be used with many resets, which makes sense. Reset styles don't typically need to enforce specificity. To avoid conflicting properties (2), it's best to continue to avoid these.
