ember-shopify-draggable
==============================================================================

Addon for using @shopify/draggable in ember projects.

![Doggie](https://media1.tenor.com/images/237857b4502f6d15cccbd58c5ca05257/tenor.gif?itemid=3501646)


- [X] Easy to use 
- [X] Fastboot Compatible (doesn't run in fastboot)
- [X] Easily Extendable

Installation
------------------------------------------------------------------------------

```
ember install ember-shopify-draggable
```


Usage
------------------------------------------------------------------------------

Right now this addon contains ember components for `swappable` and `sortable`. We hope to have full parity with all features of @shopify/draggable soon.

### Sortable functionality
This addon allows you to pass in a list object to the container component, and an item object to the item component.
This will give you the ability to keep track of the underlying JS list automatically. You can see an example of this below. 

Here we pass in list which is an array of js objects, and give `item` to each `container.item`. When any action is performed
the `group.container` component sends an action and you can just have it mutate the list. So each time the list is modified by drag/drop
your passed in list will be updated with those changes!

```
{{#sortable-group sorted=(action 'sorted') as |group|}}
    {{#group.container list
        itemReordered=(action (mut list))
        itemAdded=(action (mut list))
        itemRemoved=(action (mut list)) as |container|}}
            {{#each container.items as |item|}}
                {{#container.item item}}
                    {{item.name}}
                {{/container.item}}
            {{else}}
                Im empty
            {{/each}}
    {{/group.container}}
    {{#group.container listTwo
        itemReordered=(action (mut listTwo))
        itemAdded=(action (mut listTwo))
        itemRemoved=(action (mut listTwo)) as |container|}}
            {{#each container.items as |item|}}
                {{#container.item item}}
                    {{item.name}}
                {{/container.item}}
            {{else}}
                Im Empty
            {{/each}}
    {{/group.container}}
{{/sortable-group}}
```

Possible events for sortable can be found at [Sortable Events](https://shopify.github.io/draggable/docs/identifiers.html#sortable-sortableevent)

You can see an example of the `sorted` event being used above.

### Swappable functionality
NOTE: Currently only works with one container
```
{{#swappable-group swapped=(action 'swapped') as |group|}}
    {{#group.container list
        itemReordered=(action (mut list))
        as |container|}}
            {{#each container.items as |item index|}}
                {{#container.item item index=index}}
                    {{item.name}}
                {{/container.item}}
            {{else}}
                Im empty
            {{/each}}
    {{/group.container}}
{{/swappable-group}}
```

Possible events for swappable can be found at [Swappable Events](https://shopify.github.io/draggable/docs/identifiers.html#swappable-swappableevent)

You can see an example of the `swapped` event being used above.


Contributing
------------------------------------------------------------------------------

### Installation

* `git clone <repository-url>`
* `cd ember-shopify-draggable`
* `npm install`

### Linting

* `npm run lint:js`
* `npm run lint:js -- --fix`

### Running tests

* `ember test` – Runs the test suite on the current Ember version
* `ember test --server` – Runs the test suite in "watch mode"
* `ember try:each` – Runs the test suite against multiple Ember versions

### Running the dummy application

* `ember serve`
* Visit the dummy application at [http://localhost:4200](http://localhost:4200).

For more information on using ember-cli, visit [https://ember-cli.com/](https://ember-cli.com/).

License
------------------------------------------------------------------------------

This project is licensed under the [MIT License](LICENSE.md).
