- Start Date: 2020-05-29 
- Relevant Team(s): Ember.js
- RFC PR: (after opening the RFC PR, update this with a link to it and update the file name)
- Tracking: (leave this empty)

# Component Argument Splatting

## Summary

TODO / WIP

Allow passing arguments to a component dynamically from another variable. This feature is
analogous to object-rest-spread and argument splatting in vanilla JavaScript.

## Motivation

When making generic components, a requirement often arises to pass a number of user-defined
"extra" parameters to the component. Examples can be found in the APIs of public addons such
as:

- ember-light-table
- ember-power-select


## Detailed design

The most generic component invocation:

```
{{component nameOfComponent
  ...myHashArgs
  ...[myPositionalArgs]
}}
```

In this example, `myHashArgs` is a dictionary type containing string keys
and the values are anything that could be passed to a component argument.

Imagine that in this example, the variables contained the following values:

```
this.nameOfCompoent = 'link-to'
this.myHashArgs = {
  class: 'nova-to-memphis',
}
this.myPositionalArgs = ['See Route' 'routes.start.end' 'USA' 'Nova' 'Memphis']
```

The component invocation above would be equivalent to typing out:

```
{{link-to 'See Route' 'routes.start.end' 'USA' 'Nova' 'Memphis' class='nova-to-memphis'}}
```


```
{{component 'foo'
  thing1='foo'
  thing2='bar'
  ...otherThings
}}
```

```
{{component 'foo'
  ...otherThings
  thing1='foo'
  thing2='bar'
}}
```

```
{{#link-to nameOfRoute ...[otherThings] class='foo' ...moreParams }}
```




## How we teach this

> What names and terminology work best for these concepts and why? How is this
idea best presented? As a continuation of existing Ember patterns, or as a
wholly new one?

> Would the acceptance of this proposal mean the Ember guides must be
re-organized or altered? Does it change how Ember is taught to new users
at any level?

> How should this feature be introduced and taught to existing Ember
users?

## Drawbacks

> Why should we *not* do this? Please consider the impact on teaching Ember,
on the integration of this feature with other existing and planned features,
on the impact of the API churn on existing apps, etc.

> There are tradeoffs to choosing any path, please attempt to identify them here.

## Alternatives

> What other designs have been considered? What is the impact of not doing this?

> This section could also include prior art, that is, how other frameworks in the same domain have solved this problem.

## Unresolved questions

> Optional, but suggested for first drafts. What parts of the design are still
TBD?
