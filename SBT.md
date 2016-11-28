```js
Template.Todos_item.helpers({
  checkedClass(todo) {
    return todo.checked && 'checked';
  }
});
```

In the context of a Blaze helper, `this` is scoped to the current *data context* at the point the helper was used. This can be hard to reason about, so it's often a good idea to instead pass the required data into the helper as an argument (as we do here).

Apart from simple interpolation, mustache tags can be used for control flow in the template. For instance, in the `Lists_show` template, we render a list of todos like this:

```html
  {{#each todo in todos}}
    {{> Todos_item (todoArgs todo)}}
  {{else}}
    <div class="wrapper-message">
      <div class="title-message">No tasks here</div>
      <div class="subtitle-message">Add new tasks using the field above</div>
    </div>
  {{/each}}
```

This snippet illustrates a few things:

 - The `{% raw %}{{#each .. in}}{% endraw %}` block helper which repeats a block of HTML for each element in an array or cursor, or renders the contents of the `{% raw %}{{else}}{% endraw %}` block if no items exist.
 - The template inclusion tag, `{% raw %}{{> Todos_item (todoArgs todo)}}{% endraw %}` which renders the `Todos_item` component with the data context returned from the `todosArg` helper.

You can read about the full syntax [in the Spacebars](../api/spacebars.html). In this section we'll attempt to cover some of the important details beyond just the syntax.
