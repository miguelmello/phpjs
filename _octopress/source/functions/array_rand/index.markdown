---
layout: page
title: "JavaScript array_rand function"
comments: true
sharing: true
footer: true
sidebar: false
alias:
- /functions/view/array_rand:332
- /functions/view/array_rand
- /functions/view/332
- /functions/array_rand:332
- /functions/332
---
<!-- Generated by Rakefile:build -->
A JavaScript equivalent of PHP's array_rand

{% codeblock array/array_rand.js lang:js https://raw.github.com/kvz/phpjs/master/functions/array/array_rand.js raw on github %}
function array_rand (input, num_req) {
  // http://kevin.vanzonneveld.net
  // +   original by: Waldo Malqui Silva
  // *     example 1: array_rand( ['Kevin'], 1 );
  // *     returns 1: 0
  var indexes = [];
  var ticks = num_req || 1;
  var checkDuplicate = function (input, value) {
    var exist = false,
      index = 0,
      il = input.length;
    while (index < il) {
      if (input[index] === value) {
        exist = true;
        break;
      }
      index++;
    }
    return exist;
  };

  if (Object.prototype.toString.call(input) === '[object Array]' && ticks <= input.length) {
    while (true) {
      var rand = Math.floor((Math.random() * input.length));
      if (indexes.length === ticks) {
        break;
      }
      if (!checkDuplicate(indexes, rand)) {
        indexes.push(rand);
      }
    }
  } else {
    indexes = null;
  }

  return ((ticks == 1) ? indexes.join() : indexes);
}
{% endcodeblock %}

 - [view on github](https://github.com/kvz/phpjs/blob/master/functions/array/array_rand.js)
 - [edit on github](https://github.com/kvz/phpjs/edit/master/functions/array/array_rand.js)

### Example 1
This code
{% codeblock lang:js example %}
array_rand( ['Kevin'], 1 );
{% endcodeblock %}

Should return
{% codeblock lang:js returns %}
0
{% endcodeblock %}


### Other PHP functions in the array extension
{% render_partial _includes/custom/array.html %}
## Legacy comments
These were imported from our old site. Please use disqus below for new comments
<div style="overflow-y: scroll; max-height: 500px;">
{% render_partial functions/array_rand/_comments.html %}
</div>
