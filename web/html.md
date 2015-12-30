# Today I Learned - HTML

## Where should the 'charset' declaration be ?

In the header, within the first 1024 bytes of the document.

See [WHATWG - Charset](https://html.spec.whatwg.org/multipage/semantics.html#charset)

## PATCH/PUT/DELETE methods in a `<form>` ?

DELETE/PATCH/PUT are not valid values for the *method* attribute in the
HTML5 standard.  They were in fact
[removed from HTML4](http://www.w3.org/TR/2010/WD-html5-diff-20101019/#changes-2010-06-24)

Frameworks have a built-in work around, using for example a hidden input:

```html
<input name="_method" type="hidden" value="pacth"/>
```

* [Rails](http://guides.rubyonrails.org/form_helpers.html#how-do-forms-with-patch-put-or-delete-methods-work-questionmark)
* [Django](https://djangosnippets.org/snippets/174/)
