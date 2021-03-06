---
layout: page
title: "JavaScript bcmul function"
comments: true
sharing: true
footer: true
alias:
- /functions/view/bcmul:872
- /functions/view/bcmul
- /functions/view/872
- /functions/bcmul:872
- /functions/872
---
<!-- Generated by Rakefile:build -->
A JavaScript equivalent of PHP's bcmul

{% codeblock bc/bcmul.js lang:js https://raw.github.com/kvz/phpjs/master/functions/bc/bcmul.js raw on github %}
function bcmul(left_operand, right_operand, scale) {
  //  discuss at: http://phpjs.org/functions/bcmul/
  // original by: lmeyrick (https://sourceforge.net/projects/bcmath-js/)
  //  depends on: _phpjs_shared_bc
  //   example 1: bcmul(1, 2);
  //   returns 1: 3
  //        todo: implement these testcases

  var libbcmath = this._phpjs_shared_bc();

  var first, second, result;

  if (typeof scale === 'undefined') {
    scale = libbcmath.scale;
  }
  scale = ((scale < 0) ? 0 : scale);

  // create objects
  first = libbcmath.bc_init_num();
  second = libbcmath.bc_init_num();
  result = libbcmath.bc_init_num();

  first = libbcmath.php_str2num(left_operand.toString());
  second = libbcmath.php_str2num(right_operand.toString());

  result = libbcmath.bc_multiply(first, second, scale);

  if (result.n_scale > scale) {
    result.n_scale = scale;
  }
  return result.toString();
}
{% endcodeblock %}

 - [Raw function on GitHub](https://github.com/kvz/phpjs/blob/master/functions/bc/bcmul.js)

Please note that php.js uses JavaScript objects as substitutes for PHP arrays, they are 
the closest match to this hashtable-like data structure. 

Please also note that php.js offers community built functions and goes by the 
[McDonald's Theory](https://medium.com/what-i-learned-building/9216e1c9da7d). We'll put online 
functions that are far from perfect, in the hopes to spark better contributions. 
Do you have one? Then please just: 

 - [Edit on GitHub](https://github.com/kvz/phpjs/edit/master/functions/bc/bcmul.js)


### Other PHP functions in the bc extension
{% render_partial _includes/custom/bc.html %}
