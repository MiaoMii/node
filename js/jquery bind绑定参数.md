```js
 var iel = $("<i>", {
        class: "menu-close",
      }).bind("click", { target }, closemenu);
closemenu = function (e) {
    e.data.target
}
```

