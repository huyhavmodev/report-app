# Component and props, state

## Component note:

- Always start component names with a capital letter
- React treats components starting with lowercase letters as DOM tags. For example, `<div />` represents an HTML div tag, but `<Welcome />` represents a component and requires Welcome to be in scope.

## Props notes:

- When React sees an element representing a user-defined component, it passes JSX attributes and children to this component as a single object. We call this object `props`.

  ```jsx
  function Welcome(props) {
    return <h1>Hello, {props.name}</h1>;
  }

  const element = (
    <Welcome name="Sara">
      <h1>Hello</h1>
    </Welcome>
  );
  console.log(element.props);
  /*{
      "name":"Sara",
      "children": [
          {
            "type": "h1",
            "key": null,
            "ref": null,
            "props":{
                "children": "Hello"
            },
            "owner": null
            "_store":{}
          }
      ]
  }*/
  ReactDOM.render(element, document.getElementById("root"));
  ```

- Props are Read-Only: **All React components must act like pure functions with respect to their props**.

## State notes:

- Is similar to props, but it is private and fully controlled by the component.
- State use in statefull class components:

  ```jsx
  class Clock extends React.Component {
    constructor(props) {
      super(props);
      this.state = { date: new Date() };
    }

    render() {
      return (
        <div>
          <h1>Hello, world!</h1>
          <h2>It is {this.state.date.toLocaleTimeString()}.</h2>
        </div>
      );
    }
  }

  ReactDOM.render(<Clock />, document.getElementById("root"));
  ```
