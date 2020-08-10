
# Basic HTML and HTML5

## To remember

```html
<form action="/url-where-you-want-to-submit-form-data">
    <input type="text" placeholder="some hint" required/>

    <label for="indoor">
        <input id="indoor" type="radio" name="indoor-outdoor" value="indoor" checked/>
        indoor
    </label>

    <label for="outdoor">
        <input id="outdoor" type="radio" name="indoor-outdoor" value="outdoor"/>
        outdoor
    </label>

    <label for="apple">
        <input id="apple" type="checkbox" name="like" value="outdoor"/>
        apple
    </label>

    <label for="banana">
        <input id="banana" type="checkbox" name="like" value="outdoor"/>
        banana
    </label>

    <label for="orange">
        <input id="orange" type="checkbox" name="like" value="outdoor"/>
        orange
    </label>

    <button type="submit">Submit</button>
</form>
```

1.  `form` element need `action` attribute
1.  `input` element is self-closing
1.  `for` attribute on `label` element should match the value of `id` attribute of `input` element
1.  `name` attribute on `input` element repersent group.
