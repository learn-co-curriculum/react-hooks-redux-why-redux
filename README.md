Why Redux?
==============

In this lesson, we will learn about the Redux architecture for building web applications. By the end of the lesson you will be able to:

* Understand how Redux encourages a single source of truth.
* Understand how actions fit into the Redux flow.

## Benefits of moving to Redux

#### Single Source Of Truth

  As our React applications became larger, our state became more spread out between different components.  There are ways to get around this, like storing all of our state in a container component, but this seems to give our view the responsibility of managing our data.  In addition, you may remember the complications of passing data from a component down as props, sometimes across many levels.

Instead, Redux encourages storing all of the necessary data in our application as a plain JavaScript object called state.  It looks like this:

  ```javascript
  state = {
    user: {
      name: 'bob',
      hometown: 'philly'
    },
    interests: [
      {
        name: 'pokemon',
        type: 'game'
      },
      {
        name: 'game of thrones',
        type:'tv show'
      }
    ]
  }
  ```

This is the application state. It holds all of our data and is simply a JavaScript object.  Don't worry about this data structure taking up too much memory.  There are no methods on this object and it's pretty memory efficient.

#### How we update our state.

  So we hold the all of our data in one place.  When we want to update it, we send an action, which is a set of strict instructions Redux will use for how to update it.  

  ```javascript
  action = {
    type: 'ADD_INTEREST',
    newInterest: {
      name: 'hockey',
      type: 'sport'
    }
  }
  ```

  Here, we can imagine that after a user fills out a form and clicks submit, we will create an action that tells Redux how to incorporate the update into the state.  Any time we update the state in Redux, we must create an action first.  And this action is just a plain old JavaScript object.

  Now you can start to see how Redux allows us to update our state:

  `Action ->  State -> Updated State.`

  Just one question remains: How do we take the action, and our previously existing state, and create a new state? There must be something that puts this together.  There is, and we'll explain it in the next section.

## Summing Up

* Redux places all of our data in one place -- the state.  This state is just a plain JavaScript object.
* To change our application state, we need to first create an action that holds the information for how to update that state.
* The action, combined with the previous state, leads to an updated state.

## Resources
* [Redux Justification - Dan Abramov](https://www.youtube.com/watch?v=xsSnOQynTHs)
* [Looking back at Redux - Dan Abramov](https://www.youtube.com/watch?v=uvAXVMwHJXU)

<p class='util--hide'>View <a href='https://learn.co/lessons/why-redux'>Why Redux</a> on Learn.co and start learning to code for free.</p>
