# Declarative Events in Da3SH Markup Components

**Da3SH Declarative Events** enable javascript event listeners to be attached to DOM Elements while maintaining a _Separation of Concerns_.

Traditionally in javascript, we might implement the following inline click-handler:

## Example 1
```
<button type="button" class="myButton" onclick="myFunction1(); myFunction2();">Click Here</button>
```

Alternatively, if we want to be a little more sophisticated and make our javascript _unobtrusive_ we might remove the inline click-handler above and use `addEventListener` instead:

## Example 2
```
<button type="button" class="myButton">Click Here</button>

<script>
const myButton = document.getElementsByClassName('myButton')[0];

myButton.addEventListener('click', myFunction1, false);
myButton.addEventListener('click', myFunction2, false);
</script>
```

But this leaves us with a choice. We can either:

a) declare event listeners inline (although that requires mixing javascript in with HTML markup)
b) maintain a _Separation of Concerns_ (although that precludes being able to introduce event listeners declaratively)

What we can't achieve with either of the two approaches above is declare event listeners inline _while_ maintaining a _Separation of Concerns_.

Enter **Da3SH Declarative Events**:



```
<button type="button" class="myButton" data-events="{«data-event-1» : {«eventListener» : «click», «eventAction» : «myFunction1»}, «data-event-2» : {«eventListener» : «click», «eventAction» : «myFunction2»}}">Click Here</button>
```

All of the **Da3SH Declarative Events** are described within the `data-events` attribute, above.

It emerges that the value of the `data-events` attribute is, in fact, a quasi-`JSON` string which employs _guillemets_ (`«` and `»`) instead of double-quotes (`"` & `"`):

```
data-events="{
  
  «data-event-1» : {
    «eventListener» : «click»,
    «eventAction» : «myFunction1»
  },
  
  «data-event-2» : {
    «eventListener» : «click»,
    «eventAction» : «myFunction2»
  }
}"
```
