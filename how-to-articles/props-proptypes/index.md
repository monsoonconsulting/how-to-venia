# Props & Prop-Types
First create a child component to the Foo component we created [previously].

_src/components/Foo/greeting.js_
```javascript
import React, { Component } from 'react';
 
class Greeting extends Component {
    render() {
        return (
            <strong>Hello, {this.props.name}!</strong>
        );
    }
}
 
export default Greeting;
```

Import the Greeting component to the Foo component:   
`import Greeting from './greeting';`

Render the Greeting component in the Foo component, passing in your name as a property.    
_remember you need to wrap multiple JSX elements in a react fragment or a wrapper div_    
`<Greeting name="Joe Bloggs" />`

See the [REACT docs] for why prop types are used:   

> As your app grows, you can catch a lot of bugs with typechecking. For some applications, you can use JavaScript extensions like Flow or TypeScript to typecheck your whole application. But even if you don’t use those, React has some built-in typechecking abilities.

PWA Studio uses prop types in the following way. Import the propTypes library to the Greeting component:   
`import { PropTypes, string } from 'prop-types';`

Add type checking with a static property within the Greeting component after the opening brace:
```javascript
class Greeting extends Component {
    static propTypes = {
        name: PropTypes.string
    };
    // other code...
}
```

Try passing in an invalid prop type to the Greeting component. And check your browser console for any errors.    
i.e. `<Greeting name={2} />`

---
- [> see other topics](../../README.md#Topics)
- [> see foo-demo branch for completed code](https://github.com/rossmc/how-to-venia/tree/foo-demo/src)

[previously]: ../add-a-static-route/index.md
[REACT docs]: https://reactjs.org/docs/typechecking-with-proptypes.html