## Redux

### What is Redux ?
* Redux is a state management framework
* Redux is a predictable state container for JavaScript apps. 
* It helps to write applications that behave consistently, run in different environments (client, server, and native)
* In Redux, there is a single state object that's responsible for the entire state of the application

### store object
* The Redux `store` is an object which holds and manages application `state`
* `Redux.createStore()` is used to create Redux `store`
* This method takes a reducer function as a required argument. 
* The reducer function takes state as an argument and returns state.


[Redux: Create a Redux Store](https://learn.freecodecamp.org/front-end-libraries/redux/create-a-redux-store)

```javascript
const reducer = (state = 5) => {
  return state;
}

// Redux methods are available from a Redux object
// For example: Redux.createStore()
// Define the store here:

let store = Redux.createStore(reducer);
```


[Redux: Get State from the Redux Store](https://learn.freecodecamp.org/front-end-libraries/redux/get-state-from-the-redux-store)

* retrieve the current `state` held in the Redux `store` object with the `getState()` method.

```javascript
const store = Redux.createStore(
  (state = 5) => state
);

// change code below this line
let currentState = store.getState();
```

[Redux: Define a Redux Action](https://learn.freecodecamp.org/front-end-libraries/redux/define-a-redux-action)

* Think of Redux actions as messengers that deliver information about events happening in your app to the Redux store. 
* The store then conducts the business of updating state based on the action that occurred.
* Writing a Redux action is as simple as declaring an object with a type property.

```javascript
// Define an action here:
let action = {
  type: 'LOGIN'
}
```

[Redux: Define an Action Creator](https://learn.freecodecamp.org/front-end-libraries/redux/define-an-action-creator)

* After creating an action, the next step is sending the action to the Redux store so it can update its state.
* action creator can do it.
* **Action Creator** is simply a JavaScript function that returns an action

```javascript
const action = {
  type: 'LOGIN'
}
// Define an action creator here:

function actionCreator(){
    return action;
}
```

[Redux: Dispatch an Action Event](https://learn.freecodecamp.org/front-end-libraries/redux/dispatch-an-action-event)

* `dispatch` method  use to dispatch actions to the Redux store. 
* Calling `store.dispatch()` and passing the value returned from an action creator sends an action back to the store.

```javascript
const store = Redux.createStore(
  (state = {login: false}) => state
);

const loginAction = () => {
  return {
    type: 'LOGIN'
  }
};

// Dispatch the action here:
store.dispatch(loginAction());
```

[Redux: Handle an Action in the Store](https://learn.freecodecamp.org/front-end-libraries/redux/handle-an-action-in-the-store)

```javascript
const defaultState = {
  login: false
};

const reducer = (state = defaultState, action) => {
  // change code below this line
  if(action.type === 'LOGIN'){
    return {login: true}
  }else{
    return state;
  } 
  // change code above this line
};

const store = Redux.createStore(reducer);

const loginAction = () => {
  return {
    type: 'LOGIN'
  }
};
```

[Redux: Use a Switch Statement to Handle Multiple Actions](https://learn.freecodecamp.org/front-end-libraries/redux/use-a-switch-statement-to-handle-multiple-actions)

```javascript
const defaultState = {
  authenticated: false
};

const authReducer = (state = defaultState, action) => {
  // change code below this line
  switch (action.type) {
    case 'LOGIN':
      return { authenticated: true}
    case 'LOGOUT':
      return { authenticated: false}
    default:
      return state
  }
  // change code above this line
};

const store = Redux.createStore(authReducer);

const loginUser = () => {
  return {
    type: 'LOGIN'
  }
};

const logoutUser = () => {
  return {
    type: 'LOGOUT'
  }
};

```

[Redux: Use const for Action Types](https://learn.freecodecamp.org/front-end-libraries/redux/use-const-for-action-types)

```javascript
// change code below this line
const LOGIN = 'LOGIN';
const LOGOUT = 'LOGOUT';
// change code above this line

const defaultState = {
  authenticated: false
};

const authReducer = (state = defaultState, action) => {

  switch (action.type) {

    case LOGIN:
      return {
        authenticated: true
      }

    case LOGOUT:
      return {
        authenticated: false
      }

    default:
      return state;

  }

};

const store = Redux.createStore(authReducer);

const loginUser = () => {
  return {
    type: LOGIN
  }
};

const logoutUser = () => {
  return {
    type: LOGOUT
  }
};
```

[Redux: Register a Store Listener](https://learn.freecodecamp.org/front-end-libraries/redux/register-a-store-listener)

* `store.subscribe()` allows to subscribe listener functions to the store, which are called whenever an action is dispatched against the store.

```javascript
const ADD = 'ADD';

const reducer = (state = 0, action) => {
  switch(action.type) {
    case ADD:
      return state + 1;
    default:
      return state;
  }
};

const store = Redux.createStore(reducer);

// global count variable:
let count = 0;

// change code below this line
store.subscribe(() => {
  count = count + 1;
})
// change code above this line

store.dispatch({type: ADD});
console.log(count);
store.dispatch({type: ADD});
console.log(count);
store.dispatch({type: ADD});
console.log(count);
```

[Redux: Combine Multiple Reducers](https://learn.freecodecamp.org/front-end-libraries/redux/combine-multiple-reducers)

```javascript
const INCREMENT = 'INCREMENT';
const DECREMENT = 'DECREMENT';

const counterReducer = (state = 0, action) => {
  switch(action.type) {
    case INCREMENT:
      return state + 1;
    case DECREMENT:
      return state - 1;
    default:
      return state;
  }
};

const LOGIN = 'LOGIN';
const LOGOUT = 'LOGOUT';

const authReducer = (state = {authenticated: false}, action) => {
  switch(action.type) {
    case LOGIN:
      return {
        authenticated: true
      }
    case LOGOUT:
      return {
        authenticated: false
      }
    default:
      return state;
  }
};

const rootReducer = Redux.combineReducers({
  count: counterReducer,
  auth: authReducer
});

const store = Redux.createStore(rootReducer);
```

[Redux: Send Action Data to the Store](https://learn.freecodecamp.org/front-end-libraries/redux/send-action-data-to-the-store)

```javascript
const ADD_NOTE = 'ADD_NOTE';

const notesReducer = (state = 'Initial State', action) => {
  switch(action.type) {
    // change code below this line
    case ADD_NOTE:
      return action.text
    // change code above this line
    default:
      return state;
  }
};

const addNoteText = (note) => {
  // change code below this line
  return {
    type: ADD_NOTE,
    text: note
  }
  // change code above this line
};

const store = Redux.createStore(notesReducer);

console.log(store.getState());
store.dispatch(addNoteText('Hello!'));
console.log(store.getState());

```

[Redux: Use Middleware to Handle Asynchronous Actions](https://learn.freecodecamp.org/front-end-libraries/redux/use-middleware-to-handle-asynchronous-actions)

```javascript
const REQUESTING_DATA = 'REQUESTING_DATA'
const RECEIVED_DATA = 'RECEIVED_DATA'

const requestingData = () => { return {type: REQUESTING_DATA} }
const receivedData = (data) => { return {type: RECEIVED_DATA, users: data.users} }

const handleAsync = () => {
  return function(dispatch) {
    dispatch(requestingData());
    setTimeout(function() {
      let data = {
        users: ['Jeff', 'William', 'Alice']
      }
      dispatch(receivedData(data));
    }, 2500);
  }
};

const defaultState = {
  fetching: false,
  users: []
};

const asyncDataReducer = (state = defaultState, action) => {
  switch(action.type) {
    case REQUESTING_DATA:
      return {
        fetching: true,
        users: []
      }
    case RECEIVED_DATA:
      return {
        fetching: false,
        users: action.users
      }
    default:
      return state;
  }
};

const store = Redux.createStore(
  asyncDataReducer,
  Redux.applyMiddleware(ReduxThunk.default)
);
```

[Redux: Write a Counter with Redux](https://learn.freecodecamp.org/front-end-libraries/redux/write-a-counter-with-redux)

```javascript
const INCREMENT = 'INCREMENT'; // define a constant for increment action types
const DECREMENT = 'DECREMENT'; // define a constant for decrement action types


const counterReducer = (state = 0, action) => {
  switch(action.type){
    case INCREMENT:
      return state + 1       
    case DECREMENT:
      return state - 1
    default:
      return state
  } 
}; // define the counter reducer which will increment or decrement the state based on the action it receives

const incAction = () => {
  return {
    type: INCREMENT
  }
}; // define an action creator for incrementing

const decAction = () => {
  return {
    type: DECREMENT
  } 
}; // define an action creator for decrementing

const store = Redux.createStore(counterReducer); // define the Redux store here, passing in your reducers

```

[Redux: Never Mutate State](https://learn.freecodecamp.org/front-end-libraries/redux/never-mutate-state)

```javascript
const ADD_TO_DO = 'ADD_TO_DO';

// A list of strings representing tasks to do:
const todos = [
  'Go to the store',
  'Clean the house',
  'Cook dinner',
  'Learn to code',
];

const immutableReducer = (state = todos, action) => {
  switch(action.type) {
    case ADD_TO_DO:
      // don't mutate state here or the tests will fail
      return state.concat(action.todo)
    default:
      return state;
  }
};

// an example todo argument would be 'Learn React',
const addToDo = (todo) => {
  return {
    type: ADD_TO_DO,
    todo: todo
  }
}

const store = Redux.createStore(immutableReducer);
```

[Redux: Use the Spread Operator on Arrays](https://learn.freecodecamp.org/front-end-libraries/redux/use-the-spread-operator-on-arrays)

```
const immutableReducer = (state = ['Do not mutate state!'], action) => {
  switch(action.type) {
    case 'ADD_TO_DO':
      // don't mutate state here or the tests will fail
      return [...state, action.todo]
    default:
      return state;
  }
};

const addToDo = (todo) => {
  return {
    type: 'ADD_TO_DO',
    todo
  }
}

const store = Redux.createStore(immutableReducer);

```

[Redux: Remove an Item from an Array](https://learn.freecodecamp.org/front-end-libraries/redux/remove-an-item-from-an-array)

```javascript
const immutableReducer = (state = [0,1,2,3,4,5], action) => {
  switch(action.type) {
    case 'REMOVE_ITEM':
      // don't mutate state here or the tests will fail
      return [
        ...state.slice(0, action.index),
        ...state.slice(action.index + 1)
      ]
    default:
      return state;
  }
};

const removeItem = (index) => {
  return {
    type: 'REMOVE_ITEM',
    index
  }
}

const store = Redux.createStore(immutableReducer);
```

[Redux: Copy an Object with Object.assign](https://learn.freecodecamp.org/front-end-libraries/redux/copy-an-object-with-object-assign)

```javascript
const defaultState = {
  user: 'CamperBot',
  status: 'offline',
  friends: '732,982',
  community: 'freeCodeCamp'
};

const immutableReducer = (state = defaultState, action) => {
  switch(action.type) {
    case 'ONLINE':
      // don't mutate state here or the tests will fail
      return Object.assign({}, state, {status: 'online'})
    default:
      return state;
  }
};

const wakeUp = () => {
  return {
    type: 'ONLINE'
  }
};

const store = Redux.createStore(immutableReducer);

```