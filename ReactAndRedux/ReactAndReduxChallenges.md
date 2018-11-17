## React And Redux

[React and Redux: Getting Started with React Redux](https://learn.freecodecamp.org/front-end-libraries/react-and-redux/getting-started-with-react-redux)

```javascript
class DisplayMessages extends React.Component {
  // change code below this line
  constructor(props){
    super(props);

    this.state = {
      input: '',
      messages: []
    }
  }
  // change code above this line
  render() {
    return <div />
  }
};
```

[React and Redux: Manage State Locally First](https://learn.freecodecamp.org/front-end-libraries/react-and-redux/manage-state-locally-first)

```javascript
class DisplayMessages extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      input: '',
      messages: []
    }
    this.handleChange = this.handleChange.bind(this);
    this.submitMessage = this.submitMessage.bind(this);
  }
  // add handleChange() and submitMessage() methods here
  handleChange(event){
    this.setState({
      input: event.target.value
    });
  }
  submitMessage(){
    const currentMessage = this.state.input;
    this.setState({
      input: '',
      messages: this.state.messages.concat(currentMessage)
    })
  }
  
  render() {
    return (
      <div>
        <h2>Type in a new Message:</h2>
        { /* render an input, button, and ul here */ }
        <input value={this.state.input} onChange={this.handleChange} />
        <button onClick={this.submitMessage}>Submit</button>
        <ul>
          {
            this.state.messages.map((message, i) => {
                return(
                  <li key={i}>{message}</li>
                )
            })
          }
        </ul>
        { /* change code above this line */ }
      </div>
    );
  }
};
```

[React and Redux: Extract State Logic to Redux](https://learn.freecodecamp.org/front-end-libraries/react-and-redux/extract-state-logic-to-redux/)
```javascript
// define ADD, addMessage(), messageReducer(), and store here:

const ADD = 'ADD';

const addMessage = (message) => {
    return {
        type: ADD,
        message
    }
}

const messageReducer = (state = [], action) => {
    switch (action.type) {
        case ADD:
            return [
                ...state,
                action.message
            ];
        default:
            return state;
  }
}


const store = Redux.createStore(messageReducer);
```

[React and Redux: Use Provider to Connect Redux to React](https://learn.freecodecamp.org/front-end-libraries/react-and-redux/use-provider-to-connect-redux-to-react)

* The `Provider` is a wrapper component from `react-redux` that wraps React app. 
* This wrapper then allows to access the Redux store and dispatch functions throughout component tree. 
* `Provider` takes two props, the Redux store and the child components of the app. 

```javascript
// Redux Code:
const ADD = 'ADD';

const addMessage = (message) => {
  return {
    type: ADD,
    message
  }
};

const messageReducer = (state = [], action) => {
  switch (action.type) {
    case ADD:
      return [
        ...state,
        action.message
      ];
    default:
      return state;
  }
};



const store = Redux.createStore(messageReducer);

// React Code:

class DisplayMessages extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      input: '',
      messages: []
    }
    this.handleChange = this.handleChange.bind(this);
    this.submitMessage = this.submitMessage.bind(this);
  }
  handleChange(event) {
    this.setState({
      input: event.target.value
    });
  }
  submitMessage() {
    const currentMessage = this.state.input;
    this.setState({
      input: '',
      messages: this.state.messages.concat(currentMessage)
    });
  }
  render() {
    return (
      <div>
        <h2>Type in a new Message:</h2>
        <input
          value={this.state.input}
          onChange={this.handleChange}/><br/>
        <button onClick={this.submitMessage}>Submit</button>
        <ul>
          {this.state.messages.map( (message, idx) => {
              return (
                 <li key={idx}>{message}</li>
              )
            })
          }
        </ul>
      </div>
    );
  }
};

const Provider = ReactRedux.Provider;

class AppWrapper extends React.Component {
  // render the Provider here
    constructor(props){
        super(props)
    }
    render(){
        return (
            <Provider store={store}>
                <DisplayMessages />
            </Provider>
        )
    }
  // change code above this line
};
```

[React and Redux: Map State to Props](https://learn.freecodecamp.org/front-end-libraries/react-and-redux/map-state-to-props)

```javascript
const state = [];

// change code below this line
function mapStateToProps(state){
  return {
    messages: state
  }
}
```

[React and Redux: Map Dispatch to Props](https://learn.freecodecamp.org/front-end-libraries/react-and-redux/map-dispatch-to-props)

```javascript
const addMessage = (message) => {
  return {
    type: 'ADD',
    message: message
  }
};

// change code below this line
function mapDispatchToProps(dispatch){
    return {
        submitNewMessage: function(message){
            dispatch(addMessage(message));
        }
    }
}
```

[React and Redux: Connect Redux to React](https://learn.freecodecamp.org/front-end-libraries/react-and-redux/connect-redux-to-react)

```javascript
const addMessage = (message) => {
  return {
    type: 'ADD',
    message: message
  }
};

const mapStateToProps = (state) => {
  return {
    messages: state
  }
};

const mapDispatchToProps = (dispatch) => {
  return {
    submitNewMessage: (message) => {
      dispatch(addMessage(message));
    }
  }
};

class Presentational extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return <h3>This is a Presentational Component</h3>
  }
};

const connect = ReactRedux.connect;
// change code below this line

const ConnectedComponent = connect(mapStateToProps, mapDispatchToProps)(Presentational)

```

[React and Redux: Connect Redux to the Messages App](https://learn.freecodecamp.org/front-end-libraries/react-and-redux/connect-redux-to-the-messages-app)

```javascript
// Redux:
const ADD = 'ADD';

const addMessage = (message) => {
  return {
    type: ADD,
    message: message
  }
};

const messageReducer = (state = [], action) => {
  switch (action.type) {
    case ADD:
      return [
        ...state,
        action.message
      ];
    default:
      return state;
  }
};

const store = Redux.createStore(messageReducer);

// React:
class Presentational extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      input: '',
      messages: []
    }
    this.handleChange = this.handleChange.bind(this);
    this.submitMessage = this.submitMessage.bind(this);
  }
  handleChange(event) {
    this.setState({
      input: event.target.value
    });
  }
  submitMessage() {
    const currentMessage = this.state.input;
    this.setState({
      input: '',
      messages: this.state.messages.concat(currentMessage)
    });
  }
  render() {
    return (
      <div>
        <h2>Type in a new Message:</h2>
        <input
          value={this.state.input}
          onChange={this.handleChange}/><br/>
        <button onClick={this.submitMessage}>Submit</button>
        <ul>
          {this.state.messages.map( (message, idx) => {
              return (
                 <li key={idx}>{message}</li>
              )
            })
          }
        </ul>
      </div>
    );
  }
};

// React-Redux:
const mapStateToProps = (state) => {
  return { messages: state }
};

const mapDispatchToProps = (dispatch) => {
  return {
    submitNewMessage: (newMessage) => {
       dispatch(addMessage(newMessage))
    }
  }
};

const Provider = ReactRedux.Provider;
const connect = ReactRedux.connect;

// define the Container component here:
const Container = connect(mapStateToProps, mapDispatchToProps)(Presentational);

class AppWrapper extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    // complete the return statement:
    return (
      <Provider store={store}>
        <Container />
      </Provider>
    );
  }
};
```

[React and Redux: Extract Local State into Redux](https://learn.freecodecamp.org/front-end-libraries/react-and-redux/extract-local-state-into-redux)

```javascript
// Redux:
const ADD = 'ADD';

const addMessage = (message) => {
  return {
    type: ADD,
    message: message
  }
};

const messageReducer = (state = [], action) => {
  switch (action.type) {
    case ADD:
      return [
        ...state,
        action.message
      ];
    default:
      return state;
  }
};

const store = Redux.createStore(messageReducer);

// React:
const Provider = ReactRedux.Provider;
const connect = ReactRedux.connect;

// Change code below this line
class Presentational extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      input: ''
    }
    this.handleChange = this.handleChange.bind(this);
    this.submitMessage = this.submitMessage.bind(this);
  }
  handleChange(event) {
    this.setState({
      input: event.target.value
    });
  }
  submitMessage() {
    this.props.submitNewMessage(this.state.input);
    this.setState({
      input: '',
    });
  }
  render() {
    return (
      <div>
        <h2>Type in a new Message:</h2>
        <input
          value={this.state.input}
          onChange={this.handleChange}/><br/>
        <button onClick={this.submitMessage}>Submit</button>
        <ul>
          {this.props.messages.map( (message, idx) => {
              return (
                 <li key={idx}>{message}</li>
              )
            })
          }
        </ul>
      </div>
    );
  }
};
// Change code above this line

const mapStateToProps = (state) => {
  return {messages: state}
};

const mapDispatchToProps = (dispatch) => {
  return {
    submitNewMessage: (message) => {
      dispatch(addMessage(message))
    }
  }
};

const Container = connect(mapStateToProps, mapDispatchToProps)(Presentational);

class AppWrapper extends React.Component {
  render() {
    return (
      <Provider store={store}>
        <Container/>
      </Provider>
    );
  }
};
```

[React and Redux: Moving Forward From Here](https://learn.freecodecamp.org/front-end-libraries/react-and-redux/moving-forward-from-here)
```javascript
// import React from 'react'
// import ReactDOM from 'react-dom'
// import { Provider, connect } from 'react-redux'
// import { createStore, combineReducers, applyMiddleware } from 'redux'
// import thunk from 'redux-thunk'

// import rootReducer from './redux/reducers'
// import App from './components/App'

// const store = createStore(
//   rootReducer,
//   applyMiddleware(thunk)
// );

// ReactDOM.render(
//   <Provider store={store}>
//     <App/>
//   </Provider>,
//   document.getElementById('root')
// );

// change code below this line
console.log('Now I know React and Redux!')
```