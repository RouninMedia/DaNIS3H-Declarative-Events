# Declarative Events in DaNIS3H Markup Components

**DaNIS3H Declarative Events** enable multiple javascript event listeners (including multiple javascript event listeners of the same type) to be attached to DOM Elements while maintaining a _Separation of Concerns_.

## Example 1

Traditionally, in (old-school) javascript, we might implement the following inline click-handler:

```
<button type="button" class="myButton" onclick="myFunction1(); myFunction2();">Click Here</button>
```

## Example 2

If we want to be a little more contemporary (and sophisticated) and make our javascript _unobtrusive_ we might remove the inline click-handler above and use `addEventListener` instead:

```
<button type="button" class="myButton">Click Here</button>

<script>
const myButton = document.getElementsByClassName('myButton')[0];

myButton.addEventListener('click', myFunction1, false);
myButton.addEventListener('click', myFunction2, false);
</script>
```

But this leaves us with a choice. We can ***either***:

- declare event listeners inline (although that requires mixing javascript in with HTML markup)
- maintain a _Separation of Concerns_ (although that precludes being able to introduce event listeners declaratively)

What we ***can't achieve*** with either of the two approaches above is declare event listeners inline _while_ maintaining a _Separation of Concerns_.

We also can't declare multiple event listeners of the same type as inline HTML attributes.

Enter **DaNIS3H Declarative Events**:

```
<button type="button" class="myButton" data-events="{«click:myFunction1» : {«eventListener» : «click», «eventAction» : «myFunction1»}, «click:myFunction2» : {«eventListener» : «click», «eventAction» : «myFunction2»}}">Click Here</button>
```

All of the **DaNIS3H Declarative Events** are described within the `data-events` attribute, above.

It may be apparent that the value of the `data-events` attribute, above, is, in fact, a quasi-`JSON` string which employs _guillemets_ (`«` and `»`) instead of double-quotes (`"` & `"`), like this:

```
data-events="{
  
  «click:myFunction1» : {
    «eventListener» : «click»,
    «eventAction» : «myFunction1»
  },
  
  «click:myFunction2» : {
    «eventListener» : «click»,
    «eventAction» : «myFunction2»
  }
}"
```

_______

## Similar Ideas:

I've recently (Nov 2021) come across **htmx** which, similarly, introduces the ability to write interactivity into declarative HTML.

On first reading, though, **htmx** appears to me both (a little) more limited and (certainly) more prescriptive than **DaNIS3H Declarative Events**.

See:

 - https://htmx.org/docs/#introduction
