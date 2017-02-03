Why Redux?
==============

In this lesson, we will learn about the Redux architecture for building web applications. By the end of the lesson you will be able to:

* Understand how redux encourages single source of truth.
* Understand how actions fit into the redux flow.

## Benefits of moving to Redux

#### Single Source Of Truth

  As our react applications became larger, our state became more spread out between different  components.  There are ways to get around this like storing all of our state in a container component, but this seems to give our view the responsibility of managing our data.  In addition, you may remember the complications with passing data from a component down as props, sometimes across many levels.

	Instead, redux encourages storing all of our data necessary for our application in a plain javascript object called the state.  It looks like this:

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

It holds all of our data, and is simply a javascript object.  Don't worry about this thing taking up too much memory.  There are no methods on this object and its pretty memory efficient.

B. Clarify how we update our state

So we hold the all of our data in one place.  When we update it, redux gives us strict instructions for how to update it.  Send an action.  

```javascript
	let action = {type: 'ADD_INTEREST', payload:
		{name: 'hockey', type: 'sport'}
	}
```


#### Clarify how we update our state.

  So we hold the all of our data in one place.  When we update it, redux gives us strict instructions for how to update it.  Send an action.  

  ```javascript
  action = {
    type: 'ADD_INTEREST',
    newInterest: {
      name: 'hockey',
      type: 'sport'
    }
  }
  ```

  So we can imagine that after a user fills out a form and clicks submit, we will create an action that incorporates the update into the state.  Any time we update the state in redux, we must create an action first.  And this action is just a plain old javascript object.

  So you're starting to see how redux allows us to update our state:

  `Action ->  State -> Updated State.`

  Just one question remains: How do we take the action, and our previously existing state, and create a new state? There must be something that puts this together.  There is.  We explain it in the next section.

## Summing Up

* Redux places all of our data in one place - the state.  This state is just a plain javascript object.
* To change our application state, we need to first create an action that holds the information for how to update that state.
* The action, combined with the previous state, leads to an updated state.

## Resources
* [Redux Justification - Dan Abramov](https://www.youtube.com/watch?v=xsSnOQynTHs)
* [Looking back at Redux - Dan Abramov](https://www.youtube.com/watch?v=uvAXVMwHJXU)
