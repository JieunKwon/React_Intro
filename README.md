# React_Intro

@ Component 

We use components to tell React what we want to see on the screen. When our data changes, React will efficiently update and re-render our components.

    -- React -- 
    Declarative: 
    React makes it painless to create interactive UIs. Design simple views for each state in your application, and React will efficiently update and render just the right components when your data changes. Declarative views make your code more predictable, simpler to understand, and easier to debug.

    Component-Based: 
    Build encapsulated components that manage their own state, then compose them to make complex UIs. Since component logic is written in JavaScript instead of templates, you can easily pass rich data through your app and keep state out of the DOM.

    Learn Once, Write Anywhere: 
    We don't make assumptions about the rest of your technology stack, so you can develop new features in React without rewriting existing code. React can also render on the server using Node and power mobile apps using React Native.


@ Props

A component takes in parameters, called props (short for “properties”), and returns a hierarchy of views to display via the render method.

@ render

The render method returns a description of what you want to see on the screen.


-- Example 

    class ContactInfo extends React.Component {
      render() {
        return (
          <div>{this.props.contact.name} {this.props.contact.phone}</div>
        )
      }
    }

    class Contact extends React.Component {

      constructor(props) {
        super(props);
        this.state = {
          contactData: [
            { name: 'Abet', phone: '010-0000-0001' },
            { name: 'Betty', phone: '010-0000-0002' },
            { name: 'Charlie', phone: '010-0000-0003' },
            { name: 'David', phone: '010-0000-0004' }
          ]
        }

      }
      render() {

        const mapToComponent = (data) => {
          return data.map((contact, i) => {
            return (<ContactInfo contact={contact} key={i}/>);
          });
        };


        return (
          <div>
            { mapToComponent(this.state.contactData) }
          </div>
        );
      }
    }

    class App extends React.Component {

      render() {
        return (
          <Contact/>
        );
      }
    };

    ReactDOM.render(
      <App></App>,
      document.getElementById("root")
    );
