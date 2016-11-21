## What is the difference between String#slice(), String#substring(), String#substr() ?

The 3 methods are used to extract a portion of a String. They differ in the
interpretation of their two parameters. In every case they return a new string.

`String.prototype.slice(begin[, end])` slices the String from *begin* to (not
included) *end*.

* if *begin* or *end* are negatives, the value is considered as starting from
the end of the string.
* if *end* is greater than or equal to *begin*, an empty string is returned.

```javascript
> 'abcde'.slice(0, 4)
'abcd'

> 'abcde'.slice(-3, 4)
'cd'

> 'abcde'.slice(1,1)
''

> 'abcde'.slice(2,1)
''

> 'abcde'.slice()
'abcde'
```

`String.prototype.substring(begin[, end])` returns a subset of the String
between *begin* to (not included) *end*.

* negative or NaN values are treated as 0.
* if *end* is greater than or equal to *begin*, it is as if the two arguments
were swapped (i.e `'abcd'.subtring(2,1) === 'abc'.substring(1,2)`).

```javascript
> 'abcde'.substring(0, 4)
'abcd'

> 'abcde'.substring(-3, 4)
'abcd'

> 'abcde'.substring(1,1)
''

> 'abcde'.substring(2,1)
'b'

> 'abcde'.substring()
'abcde'
```

`String.prototype.substr(start[, length])` returns the character in a string
starting at *start*, with the given length.

* if *start* is negative, the value is considered as starting from the end of
the string.

```javascript
> 'abcde'.substr(0, 4)
'abcd'

> 'abcde'.substr(-3, 4)
'cde'

> 'abcde'.substr(1,1)
'b'

> 'abcde'.substr(2,1)
'c'

> 'abcde'.substr()
'abcde'
```

See [MDN - String.prototype.slice()](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/String/slice)
See [MDN - String.prototype.substring()](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/String/substring)
See [MDN - String.prototype.substr()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/substr)
