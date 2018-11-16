JSX

[React: Create a Simple JSX Element](https://learn.freecodecamp.org/front-end-libraries/react/create-a-simple-jsx-element)


[
React: Create a Complex JSX Element](https://learn.freecodecamp.org/front-end-libraries/react/create-a-complex-jsx-element)

* Nested JSX must return single element.
* This parent element would wrap all the other levels of nested elements

[React: Add Comments in JSX](https://learn.freecodecamp.org/front-end-libraries/react/add-comments-in-jsx)

* comments inside JSX `{/* */}`


```javascript
const JSX = (
  <div>
    <h1>This is a block of JSX</h1>
    <p>Here's a subtitle</p>
    {/* This is comment */}
  </div>
);

```

[React: Render HTML Elements to the DOM](https://learn.freecodecamp.org/front-end-libraries/react/render-html-elements-to-the-dom)

```javascript
const JSX = (
  <div>
    <h1>Hello World</h1>
    <p>Lets render this to the DOM</p>
  </div>
);
// change code below this line

ReactDOM.render(JSX, document.getElementById("challenge-node"));

```

[React: Define an HTML Class in JSX](https://learn.freecodecamp.org/front-end-libraries/react/define-an-html-class-in-jsx)

* the naming convention for all HTML attributes and event references in JSX become camelCase. For example, a click event in JSX is onClick, instead of onclick

```javascript
const JSX = (
  <div className="myDiv">
    <h1>Add a class to this div</h1>
  </div>
);
```

[React: Learn About Self-Closing JSX Tags](https://learn.freecodecamp.org/front-end-libraries/react/learn-about-self-closing-jsx-tags)

* In JSX, Any JSX element can be written with a self-closing tag, and every element must be closed. 
* The line-break tag, for example, must always be written as <br /> in order to be valid JSX that can be transpiled

```javascript
const JSX = (
  <div>
    <h2>Welcome to React!</h2> <br />
    <p>Be sure to close all tags!</p>
    <hr /> 
  </div>
);
```

[React: Create a Stateless Functional Component](https://learn.freecodecamp.org/front-end-libraries/react/create-a-stateless-functional-component)

* Two way to create React Component
    1. JavaScript Function
        - It will create stateless functional component
        - **Stateless Components** : stateless component as one that can receive data and render it, but does not manage or track changes to that data. 
        - **How to create ?**
            - write a JavaScript function that returns either JSX or null
            - function name should begin with a capital letter
    2. Using class syntax


```javascript
const MyComponent = function() {
  return (
    <div>
      <p>Some paragraph text</p>
    </div>
  )
};
```

[React: Create a React Component](https://learn.freecodecamp.org/front-end-libraries/react/create-a-react-component)


```javascript
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h1>Hello React!</h1>
      </div>
    );
  }
};
```

[React: Create a Component with Composition](https://learn.freecodecamp.org/front-end-libraries/react/create-a-component-with-composition)

```javascript
const ChildComponent = () => {
  return (
    <div>
      <p>I am the child</p>
    </div>
  );
};

class ParentComponent extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h1>I am the parent</h1>
        { /* change code below this line */ }
        <ChildComponent />

        { /* change code above this line */ }
      </div>
    );
  }
};
```

[React: Use React to Render Nested Components](https://learn.freecodecamp.org/front-end-libraries/react/use-react-to-render-nested-components)

```javascript
const TypesOfFruit = () => {
  return (
    <div>
      <h2>Fruits:</h2>
      <ul>
        <li>Apples</li>
        <li>Blueberries</li>
        <li>Strawberries</li>
        <li>Bananas</li>
      </ul>
    </div>
  );
};

const Fruits = () => {
  return (
    <div>
      { /* change code below this line */ }
      <TypesOfFruit />
      { /* change code above this line */ }
    </div>
  );
};

class TypesOfFood extends React.Component {
  constructor(props) {
    super(props);
  }

  render() {
    return (
      <div>
        <h1>Types of Food:</h1>
        { /* change code below this line */ }
        <Fruits />
        { /* change code above this line */ }
      </div>
    );
  }
};
```

[React: Compose React Components](https://learn.freecodecamp.org/front-end-libraries/react/compose-react-components)

```javascript
class Fruits extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h2>Fruits:</h2>
        { /* change code below this line */ }
        <NonCitrus />
        <Citrus />
         { /* change code above this line */ }
      </div>
    );
  }
};

class TypesOfFood extends React.Component {
  constructor(props) {
     super(props);
  }
  render() {
    return (
      <div>
        <h1>Types of Food:</h1>
        { /* change code below this line */ }
        <Fruits />
        { /* change code above this line */ }
        <Vegetables />
      </div>
    );
  }
};
```

[React: Render a Class Component to the DOM](https://learn.freecodecamp.org/front-end-libraries/react/render-a-class-component-to-the-dom)

```javascript

class TypesOfFood extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h1>Types of Food:</h1>
        {/* change code below this line */}
        <Fruits />
        <Vegetables />
        {/* change code above this line */}
      </div>
    );
  }
};

// change code below this line
ReactDOM.render(<TypesOfFood />, document.getElementById("challenge-node"));

```

[React: Write a React Component from Scratch](https://learn.freecodecamp.org/front-end-libraries/react/write-a-react-component-from-scratch)

```javascript
// change code below this line

class MyComponent extends React.Component {
  constructor(props){
    super(props);
  }
  render(){
    return (
      <div>
        <h1>My First React Component!</h1>
      </div>
    )
  } 
}

ReactDOM.render(<MyComponent />, document.getElementById('challenge-node'));
```

[React: Pass Props to a Stateless Functional Component](https://learn.freecodecamp.org/front-end-libraries/react/pass-props-to-a-stateless-functional-component)

```javascript

const CurrentDate = (props) => {
  return (
    <div>
      { /* change code below this line */ }
      <p>The current date is: {props.date}</p>
      { /* change code above this line */ }
    </div>
  );
};

class Calendar extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h3>What date is it?</h3>
        { /* change code below this line */ }
        <CurrentDate date={Date()} />
        { /* change code above this line */ }
      </div>
    );
  }
};
```

[React: Pass an Array as Props](https://learn.freecodecamp.org/front-end-libraries/react/pass-an-array-as-props)

```javascript
const List= (props) => {
  { /* change code below this line */ }
  return <p>{props.tasks.join(', ')}</p>
  { /* change code above this line */ }
};

class ToDo extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h1>To Do Lists</h1>
        <h2>Today</h2>
        { /* change code below this line */ }
        <List tasks={["walk dog", "workout"]}/>
        <h2>Tomorrow</h2>
        <List tasks={["walk dog", "workout", "fun"]}/>
        { /* change code above this line */ }
      </div>
    );
  }
};

```

[React: Use Default Props](https://learn.freecodecamp.org/front-end-libraries/react/use-default-props)

```javascript
const ShoppingCart = (props) => {
  return (
    <div>
      <h1>Shopping Cart Component</h1>
    </div>
  )
};
// change code below this line
ShoppingCart.defaultProps = {
  items: 0
}
```

[React: Override Default Props](https://learn.freecodecamp.org/front-end-libraries/react/override-default-props)

```javascript
const Items = (props) => {
  return <h1>Current Quantity of Items in Cart: {props.quantity}</h1>
}

Items.defaultProps = {
  quantity: 0
}

class ShoppingCart extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    { /* change code below this line */ }
    return <Items quantity={10}/>
    { /* change code above this line */ }
  }
};
```

[React: Use PropTypes to Define the Props You Expect](https://learn.freecodecamp.org/front-end-libraries/react/use-proptypes-to-define-the-props-you-expect)

```javascript
const Items = (props) => {
  return <h1>Current Quantity of Items in Cart: {props.quantity}</h1>
};

// change code below this line
Items.propTypes = {
  quantity: PropTypes.number.isRequired
}
// change code above this line

Items.defaultProps = {
  quantity: 0
};

class ShoppingCart extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return <Items />
  }
};

```

[React: Access Props Using this.props](https://learn.freecodecamp.org/front-end-libraries/react/access-props-using-this-props)

```javascript
class ReturnTempPassword extends React.Component {
  constructor(props) {
    super(props);

  }
  render() {
    return (
        <div>
            { /* change code below this line */ }
            <p>Your temporary password is: <strong>{this.props.tempPassword}</strong></p>
            { /* change code above this line */ }
        </div>
    );
  }
};

class ResetPassword extends React.Component {
  constructor(props) {
    super(props);

  }
  render() {
    return (
        <div>
          <h2>Reset Password</h2>
          <h3>We've generated a new temporary password for you.</h3>
          <h3>Please reset this password from your account settings ASAP.</h3>
          { /* change code below this line */ }
          <ReturnTempPassword tempPassword={'Pass#2018'} />
          { /* change code above this line */ }
        </div>
    );
  }
};
```

[React: Review Using Props with Stateless Functional Components](https://learn.freecodecamp.org/front-end-libraries/react/review-using-props-with-stateless-functional-components)

- **A stateless functional component** is any function  which accepts props and returns JSX. 
- **A stateless component**, on the other hand, is a class that extends React.Component, but does not use internal state.
- **A stateful component** is any component that does maintain its own internal state.
- stateful components referred to simply as components or React components.

```javascript
class CampSite extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <Camper/>
      </div>
    );
  }
};
// change code below this line

class Camper extends React.Component {
  constructor(props){
    super(props);
  }
  render(){
    return(
      <p>{this.props.name}</p>
    )
  }
}

Camper.defaultProps = {
  name: 'CamperBot'
}

Camper.propTypes = {
  name: PropTypes.string.isRequired
}
```

[React: Create a Stateful Component](https://learn.freecodecamp.org/front-end-libraries/react/create-a-stateful-component)

```javascript

class StatefulComponent extends React.Component {
  constructor(props) {
    super(props);
    // initialize state here
    this.state = {
      name : "Vivan"
    }
  }
  render() {
    return (
      <div>
        <h1>{this.state.name}</h1>
      </div>
    );
  }
};
```

[React: Render State in the User Interface](https://learn.freecodecamp.org/front-end-libraries/react/render-state-in-the-user-interface)

```javascript
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: 'freeCodeCamp'
    }
  }
  render() {
    return (
      <div>
        { /* change code below this line */ }
        <h1>{ this.state.name }</h1>
        { /* change code above this line */ }
      </div>
    );
  }
};
```

[React: Render State in the User Interface Another Way](https://learn.freecodecamp.org/front-end-libraries/react/render-state-in-the-user-interface-another-way)

```javascript
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: 'freeCodeCamp'
    }
  }
  render() {
    // change code below this line
    const name = this.state.name;
    // change code above this line
    return (
      <div>
        { /* change code below this line */ }
        <h1>{name}</h1>
        { /* change code above this line */ }
      </div>
    );
  }
};
```

[React: Set State with this.setState](https://learn.freecodecamp.org/front-end-libraries/react/set-state-with-this-setstate)

```javascript
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: 'Initial State'
    };
    this.handleClick = this.handleClick.bind(this);
  }
  handleClick() {
    // change code below this line
    this.setState({
      name: 'React Rocks!'
    })
    // change code above this line
  }
  render() {
    return (
      <div>
        <button onClick={this.handleClick}>Click Me</button>
        <h1>{this.state.name}</h1>
      </div>
    );
  }
};
```

[React: Bind 'this' to a Class Method](https://learn.freecodecamp.org/front-end-libraries/react/bind-this-to-a-class-method)

```javascript
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      itemCount: 0
    };
    // change code below this line
    this.addItem = this.addItem.bind(this);
    // change code above this line
  }
  addItem() {
    this.setState({
      itemCount: this.state.itemCount + 1
    });
  }
  render() {
    return (
      <div>
        { /* change code below this line */ }
        <button onClick={this.addItem}>Click Me</button>
        { /* change code above this line */ }
        <h1>Current Item Count: {this.state.itemCount}</h1>
      </div>
    );
  }
};
```

[React: Use State to Toggle an Element](https://learn.freecodecamp.org/front-end-libraries/react/use-state-to-toggle-an-element)

```javascript
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      visibility: false
    };
    // change code below this line
    this.toggleVisibility = this.toggleVisibility.bind(this);
    // change code above this line
  }
  // change code below this line
  toggleVisibility(){
    this.setState({
      visibility : !this.state.visibility
    });
  }
  // change code above this line
  render() {
    if (this.state.visibility) {
      return (
        <div>
          <button onClick={this.toggleVisibility}>Click Me</button>
          <h1>Now you see me!</h1>
        </div>
      );
    } else {
      return (
        <div>
          <button onClick={this.toggleVisibility}>Click Me</button>
        </div>
      );
    }
  }
};
```

[React: Write a Simple Counter](https://learn.freecodecamp.org/front-end-libraries/react/write-a-simple-counter)

```javascript
class Counter extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0
    };
    // change code below this line
    this.increment = this.increment.bind(this);
    this.decrement = this.decrement.bind(this);
    this.reset = this.reset.bind(this);
    // change code above this line
  }
  // change code below this line
  increment(){
    this.setState({
      count: this.state.count + 1
    })
  }
  decrement(){
    this.setState({
      count: this.state.count - 1
    })
  }
  reset(){
    this.setState({
      count: 0
    })
  }
  // change code above this line
  render() {
    return (
      <div>
        <button className='inc' onClick={this.increment}>Increment!</button>
        <button className='dec' onClick={this.decrement}>Decrement!</button>
        <button className='reset' onClick={this.reset}>Reset</button>
        <h1>Current Count: {this.state.count}</h1>
      </div>
    );
  }
};

```

[React: Create a Controlled Input](https://learn.freecodecamp.org/front-end-libraries/react/create-a-controlled-input)

```javascript
class ControlledInput extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      input: ''
    };
    // change code below this line
    this.handleChange = this.handleChange.bind(this);
    // change code above this line
  }
  // change code below this line
  handleChange(event){
    this.setState({
      input: event.target.value
    })
  }
  // change code above this line
  render() {
    return (
      <div>
        { /* change code below this line */}
        <input type="text" value={this.state.input} onChange={this.handleChange} />
        { /* change code above this line */}
        <h4>Controlled Input:</h4>
        <p>{this.state.input}</p>
      </div>
    );
  }
};
```

[React: Create a Controlled Form](https://learn.freecodecamp.org/front-end-libraries/react/create-a-controlled-form)

```javascript
class MyForm extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      input: '',
      submit: ''
    };
    this.handleChange = this.handleChange.bind(this);
    this.handleSubmit = this.handleSubmit.bind(this);
  }
  handleChange(event) {
    this.setState({
      input: event.target.value
    });
  }
  handleSubmit(event) {
    // change code below this line
    this.setState({
      submit: this.state.input
    });
    event.preventDefault();
    // change code above this line
  }
  render() {
    return (
      <div>
        <form onSubmit={this.handleSubmit}>
          { /* change code below this line */ }
          <input type="text" value={this.state.input} onChange={this.handleChange} />
          { /* change code above this line */ }
          <button type='submit'>Submit!</button>
        </form>
        { /* change code below this line */ }
        <h1>{this.state.submit}</h1>
        { /* change code above this line */ }
      </div>
    );
  }
};

```

[React: Pass State as Props to Child Components](https://learn.freecodecamp.org/front-end-libraries/react/pass-state-as-props-to-child-components)

```javascript
class MyApp extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: 'CamperBot'
    }
  }
  render() {
    return (
       <div>
         <Navbar name={this.state.name} />
       </div>
    );
  }
};

class Navbar extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
    <div>
      <h1>Hello, my name is: {this.props.name} </h1>
    </div>
    );
  }
};
```

[React: Pass a Callback as Props](https://learn.freecodecamp.org/front-end-libraries/react/pass-a-callback-as-props)

```javascript
class MyApp extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      inputValue: ''
    }
    this.handleChange = this.handleChange.bind(this);
  }
  handleChange(event) {
    this.setState({
      inputValue: event.target.value
    });
  }
  render() {
    return (
       <div>
        { /* change code below this line */ }
        <GetInput input={this.state.inputValue} handleChange={this.handleChange}/>
        <RenderInput input={this.state.inputValue}/>
        { /* change code above this line */ }
       </div>
    );
  }
};

class GetInput extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h3>Get Input:</h3>
        <input
          value={this.props.input}
          onChange={this.props.handleChange}/>
      </div>
    );
  }
};

class RenderInput extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h3>Input Render:</h3>
        <p>{this.props.input}</p>
      </div>
    );
  }
};
```




