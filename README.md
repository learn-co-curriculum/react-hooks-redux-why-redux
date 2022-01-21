# Why Redux?

## Learning Goals

- Explain how Redux encourages a single source of truth
- Explain how actions fit into the Redux flow

## Introduction

In this lesson, we will learn about the Redux architecture for building web
applications.

## Benefits of Moving to Redux

As our React applications become larger, our state becomes more spread out
between different components. At a certain point, the component tree becomes a
web of props and state that can obscure our view of how components are handling
and sharing data with each other.

There are ways to get around this, like storing all of our state in one high
level container component, but this can ultimately _increase_ the complexity of
your props.

Redux offers a different solution. It encourages storing all of the shared state
in our application in a JavaScript object _separate_ from our components known
as the **store**. Picture having all your shared application state in one big
object, like this:

```javascript
store = {
  user: {
    name: "bob",
    hometown: "philly",
  },
  interests: [
    {
      name: "pokemon",
      type: "game",
    },
    {
      name: "game of thrones",
      type: "tv show",
    },
  ],
};
```

Similar to component state, all our data can be held in an object. The
difference here is that, since Redux state is separate from the component tree,
we can grab _any_ part of this data for _any_ component that needs it, just by
connecting the component! Using Redux means we have a **single source of truth**
for our application's state.

## Accessing Our State

To make this state available for components to connect to, we provide access by
wrapping the component tree with a special context provider component, similar
to the `BrowserRouter` component we used with React Router. This gives us access
to Redux hooks that allow us to access the Redux store from any component.

Consequently, complex interaction between components is made easier. Take for
example sibling components (rendered side by side in a parent) and cousin
components (the children of sibling components). Without Redux, if siblings are
both displaying or manipulating the same bit of shared data, that data needs to
be stored in their parent component's state. If _cousins_ are sharing data, the
data needs to be stored in the _grandparent_ component, the closest shared
'ancestor' component.

With Redux, all these interactions are structured the same way. Every component
we allow can get and update state from the Redux store regardless of the
position of components in a tree.

## Updating Our State

With Redux, we hold all of our shared state in one place and with some
configuration, we can read it via hooks in regular React components.

When we want to update that shared state, we must send an action, which is a set
of strict instructions _we create_ that tells Redux how to update our state.

```javascript
action = {
  type: "interests/addInterest",
  payload: {
    name: "hockey",
    type: "sport",
  },
};
```

Here, we can imagine that after a user fills out a form and clicks submit, we
will create an action that tells Redux how to incorporate the update into the
state. Any time we update state with Redux, we must create an action first. This
action is just a plain old JavaScript object.

These actions are used by our components. Any component will be able to modify
state in the Redux store using an action we've defined by **dispatching** the
action to the Redux store.

Following a specific design pattern that we'll explore through the upcoming
lessons, we can use these actions to update our Redux state. These state changes
trigger re-renders in our components so that they can display the updated state.

## Conclusion

Redux places all of our data in one place — the store. This store is just a
plain JavaScript object representing the shared global state for our
application. In fact, all the pieces of Redux are plain old JavaScript. It is
the pattern, the way the information flows, that makes Redux awesome.

To change our application state, we need to create an action that defines how to
update that state. The action, combined with the previous state, produces an
updated state.

## Resources

- [Redux Justification - Dan Abramov](https://www.youtube.com/watch?v=xsSnOQynTHs)
- [Looking back at Redux - Dan Abramov](https://www.youtube.com/watch?v=uvAXVMwHJXU)
