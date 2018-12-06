Redux is a predictable state container for JavaScript apps.

#### Action
Action is dispatched from Components. They are objects that contain a `type` and `payload`.

#### Reducer
Reducer is a function that can update the central store. It accepts the action and old state as input. Reducer function is synchronous and should not contain in side effects like AJAX calls.

When the store is updated, Redux triggers all subscribed components and pass the current store state as props to these components.

## Different steps on how redux works
```javascript
const redux = require('redux');

const initialState = {
  counter: 0
}

// Reducer. This reducer is called when each action is dispatched.
const rootReducer = (state = initialState, action) => {
  if (action.type === 'INC_COUNTER') {
    return {
      ...state,
      counter: state.counter + 1
    }
  }
  if (action.type === 'ADD_COUNTER') {
    return {
      ...state,
      counter: state.counter + action.value
    }
  }
  return state;
}

// Store
const store = redux.createStore(rootReducer);
console.log(store.getState());

// Subscription. This is needed before dispatching.
store.subscribe(() => {
  console.log('[Subscribe]:', store.getState());
});

// Dispatching Action
store.dispatch({type: 'INC_COUNTER'});
store.dispatch({type: 'ADD_COUNTER', value: 10});
console.log(store.getState());
```
