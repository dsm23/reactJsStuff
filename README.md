# Basics

```javascript
const h1 = <h1>Hello world</h1>;
```

## JSX elements

```javascript
const multiLine = (
	<div>
		<p>Hello</p>
		<p>World</p>
	</div>
)
```

## ReactDOM
```javascript
import React from 'react';
import ReactDOM from 'react-dom';

// This is just an example, switch to app.js for the exercise.
ReactDOM.render(
	<h1>Hello world</h1>,
	document.getElementById('app')
);
```

```javascript
import React from 'react';
import ReactDOM from 'react-dom';

// Write code here:
const myList = (
	<ul>
    <li>a</li>
    <li>b</li>
  </ul>
)

ReactDOM.render(
	myList,
  document.getElementById('app')
);
```

https://www.codecademy.com/articles/react-virtual-dom

# Advanced JSX

## className

```javascript
import React from 'react';
import ReactDOM from 'react-dom';

// Write code here:
const myDiv = <div className="big">I AM A BIG DIV</div>;

ReactDOM.render(
	myDiv,
  document.getElementById('app')
);
```

## Self-closing HTML Tags
```javascript
const profile = (
  <div>
    <h1>I AM JENKINS</h1>
    <img src="images/jenkins.png" /> // <img> does not work
    <article>
      I LIKE TO SIT
      <br /> // <br> does not work
      JENKINS IS MY NAME
      <br /> // <br> does not work
      THANKS HA LOT
    </article>
  </div>
);
```

## Vanilla JS inside ReactJS
```javascript
import React from 'react';
import ReactDOM from 'react-dom';

// Write code here:
ReactDOM.render(
	<h1>{2 + 3}</h1>,
  document.getElementById('app')
);
```

```javascript
import React from 'react';
import ReactDOM from 'react-dom';

const theBestString = 'tralalalala i am da best';

ReactDOM.render(
  <h1>{theBestString}</h1>,
  document.getElementById('app')
);
```

## eventListeners are written in camelCase

```javascript
import React from 'react';
import ReactDOM from 'react-dom';

function makeDoggy(e) {
  // Call this extremely useful function on an <img>.
  // The <img> will become a picture of a doggy.
  e.target.setAttribute('src', 'https://s3.amazonaws.com/codecademy-content/courses/React/react_photo-puppy.jpeg');
  e.target.setAttribute('alt', 'doggy');
}

const kitty = (
	<img 
		src="https://s3.amazonaws.com/codecademy-content/courses/React/react_photo-kitty.jpg" 
		alt="kitty"
    onClick={makeDoggy} />
);

ReactDOM.render(
  kitty,
  document.getElementById('app')
);
```

## if statements

http://facebook.github.io/react/tips/if-else-in-JSX.html

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let

```javascript
import React from 'react';
import ReactDOM from 'react-dom';

function coinToss() {
  // This function will randomly return either 'heads' or 'tails'.
  return Math.random() < 0.5 ? 'heads' : 'tails';
}

const pics = {
  kitty: 'https://s3.amazonaws.com/codecademy-content/courses/React/react_photo-kitty.jpg',
  doggy: 'https://s3.amazonaws.com/codecademy-content/courses/React/react_photo-puppy.jpeg'
};
let img;

// if/else statement begins here:
if (coinToss() === 'heads') {
  img = <img src={pics.kitty} />
} else {
  img = <img src={pics.doggy} />
}

ReactDOM.render(
	img,
  document.getElementById('app')
);
```

https://stackoverflow.com/questions/6259982/how-do-you-use-the-conditional-operator-in-javascript

Ternary operator

```javascript
import React from 'react';
import ReactDOM from 'react-dom';

function coinToss () {
  // Randomly return either 'heads' or 'tails'.
  return Math.random() < 0.5 ? 'heads' : 'tails';
}

const pics = {
  kitty: 'https://s3.amazonaws.com/codecademy-content/courses/React/react_photo-kitty.jpg',
  doggy: 'https://s3.amazonaws.com/codecademy-content/courses/React/react_photo-puppy.jpeg'
};

const img = <img src={pics[coinToss()==='heads' ? 'kitty' : 'doggy']} />;

ReactDOM.render(
	img, 
	document.getElementById('app')
);
```

## && operator

!judgmental should come before the && operator.

```javascript
import React from 'react';
import ReactDOM from 'react-dom';

// judgmental will be true half the time.
const judgmental = Math.random() < 0.5;

const favoriteFoods = (
  <div>
    <h1>My Favorite Foods</h1>
    <ul>
      <li>Sushi Burrito</li>
      <li>Rhubarb Pie</li>
      { !judgmental && <li>Nacho Cheez Straight Out The Jar</li> }
      <li>Broiled Grapefruit</li>
    </ul>
  </div>
);

ReactDOM.render(
	favoriteFoods, 
	document.getElementById('app')
);
```

## .map

```javascript
import React from 'react';
import ReactDOM from 'react-dom';

const people = ['Rowe', 'Prevost', 'Gare'];

const peopleLis = people.map(person =>
  // expression goes here:
<li>{person}</li>;
);

// ReactDOM.render goes here:
ReactDOM.render(
	<ul>{peopleLis}</ul>,
  document.getElementById('app')
);
```

## keys

```javascript
import React from 'react';
import ReactDOM from 'react-dom';

const people = ['Rowe', 'Prevost', 'Gare'];

const peopleLis = people.map((person,i) =>
  // expression goes here:
<li key={'person_' + i}>{person}</li>;
);

// ReactDOM.render goes here:
ReactDOM.render(
	<ul>{peopleLis}</ul>,
  document.getElementById('app')
);
```

## createElement

not JSX

https://reactjs.org/docs/react-api.html#react.createelement

```javascript
const greatestDivEver = React.createElement(
	"div",
  null,
  "i am div"
);
```

# Classes and Components

```javascript
import React from 'react';
import ReactDOM from 'react-dom';

class MyComponentClass extends React.Component {
  render() {
    return <h1>Hello world</h1>;
  }
}

// component goes here:
ReactDOM.render(
  <MyComponentClass />,
  document.getElementById('app')
);
```
QuoteMaker
```javascript
import React from 'react';
import ReactDOM from 'react-dom';

class QuoteMaker extends React.Component {
  render() {
    return (
      <blockquote>
        <p>
          The world is full of objects, more or less interesting; I do not wish to add any more.
        </p>
        <cite>
          <a target="_blank"
            href="http://bit.ly/1WGzM4G">
            Douglas Huebler
          </a>
        </cite>
      </blockquote>
    );
  }
};

ReactDOM.render(
  <QuoteMaker />,
  document.getElementById('app')
);
```

ReactJs accepts newlines in its syntax

```javascript
import React from 'react';
import ReactDOM from 'react-dom';


const owl = {
  title: "Excellent Owl",
  src: "https://s3.amazonaws.com/codecademy-content/courses/React/react_photo-owl.jpg"
};

// Component class starts here:
class Owl extends React.Component{
  render(){
    return (
    	<div>
        <h1>{owl.title}</h1>
        <img 
          src={owl.src}
          alt={owl.title} />
      </div>
    );
  }
}

ReactDOM.render(
	<Owl />,
  document.getElementById('app')
);
```

```javascript
import React from 'react';
import ReactDOM from 'react-dom';


const friends = [
  {
    title: "Yummmmmmm",
    src: "https://s3.amazonaws.com/codecademy-content/courses/React/react_photo-monkeyweirdo.jpg"
  },
  {
    title: "Hey Guys!  Wait Up!",
    src: "https://s3.amazonaws.com/codecademy-content/courses/React/react_photo-earnestfrog.jpg"
  },
  {
    title: "Yikes",
    src: "https://s3.amazonaws.com/codecademy-content/courses/React/react_photo-alpaca.jpg"
  }
];

// New component class starts here:
class Friend extends React.Component{
  render() {
    const friend = friends[1];
    return (
    	<div>
        <h1>{friend.title}</h1>
        <img 
          src={friend.src} />
    	</div>
    );
  }
}

ReactDOM.render(
  <Friend />,
  document.getElementById('app')
);
```

plain javascript can go within a render method but outside of the return statement

```javascript
import React from 'react';
import ReactDOM from 'react-dom';

const fiftyFifty = Math.random() < 0.5;

// New component class starts here:
class TonightsPlan extends React.Component{
  render(){
    if (fiftyFifty){
      return <h1>Tonight I'm going out WOOO</h1>
    }
    else {
      return <h1>Tonight I'm going to bed WOOO</h1>
    }
  }
}

ReactDOM.render(
  <TonightsPlan />,
  document.getElementById('app')
);
```
## this and getters

```javascript
import React from 'react';
import ReactDOM from 'react-dom';

class MyName extends React.Component {
	// name property goes here:
get name() {
  return 'David Murdoch';
}

  render() {
    return <h1>My name is {this.name}.</h1>;
  }
}

ReactDOM.render(<MyName />, document.getElementById('app'));
```

## this and eventListeners

```javascript
import React from 'react';
import ReactDOM from 'react-dom';

class Button extends React.Component {
  scream() {
    alert('AAAAAAAAHHH!!!!!');
  }

  render() {
    return <button onClick={this.scream}>AAAAAH!</button>;
  }
}

ReactDOM.render(<Button />,document.getElementById('app'));
```

# Components render other Components

import a Component from one file to another

for NavBar.js:

```javascript
import React from 'react';

export class NavBar extends React.Component {
  render() {
    const pages = ['home', 'blog', 'pics', 'bio', 'art', 'shop', 'about', 'contact'];
    const navLinks = pages.map(page => {
      return (
        <a href={'/' + page}>
          {page}
        </a>
      )
    });

    return <nav>{navLinks}</nav>;
  }
}
```
then for ProfilePage.js:

```javascript
import React from 'react';
import ReactDOM from 'react-dom';
import { NavBar} from './NavBar.js'


class ProfilePage extends React.Component {
  render() {
    return (
      <div>
				<NavBar />
        <h1>All About Me!</h1>
        <p>I like movies and blah blah blah blah blah</p>
        <img src="https://s3.amazonaws.com/codecademy-content/courses/React/react_photo-monkeyselfie.jpg" />
      </div>
    );
  }
}

ReactDOM.render(
	<ProfilePage />,
  document.getElementById('app')
);
```

http://exploringjs.com/es6/ch_modules.html

# this.props

```javascript
import React from 'react';
import ReactDOM from 'react-dom';

class PropsDisplayer extends React.Component {
  render() {
  	const stringProps = JSON.stringify(this.props);

    return (
      <div>
        <h1>CHECK OUT MY PROPS OBJECT</h1>
        <h2>{stringProps}</h2>
      </div>
    );
  }
}

// ReactDOM.render goes here:
ReactDOM.render(
	<PropsDisplayer myProp="Hello" />,
  document.getElementById('app')
);
```

```javascript
import React from 'react';
import ReactDOM from 'react-dom';

class Greeting extends React.Component {
  render() {
    return <h1>Hi there, {this.props.firstName}!</h1>;
  }
}

ReactDOM.render(
  <Greeting firstName='David' />, 
  document.getElementById('app')
);
```

Greeting.js
```javascript
import React from 'react';

export class Greeting extends React.Component {
  render() {
    return <h1>Hi there, {this.props.name}!</h1>;
  }
}
```

App.js
```javascript
import React from 'react';
import ReactDOM from 'react-dom';
import { Greeting } from './Greeting.js'

class App extends React.Component {
  render() {
    return (
      <div>
        <h1>
          Hullo and, "Welcome to The Newzz," "On Line!"
        </h1>
        <Greeting name="David" />
        
        <article>
          Latest newzz:  where is my phone?
        </article>
      </div>
    );
  }
}

ReactDOM.render(
  <App />, 
  document.getElementById('app')
);
```

https://mathiasbynens.be/notes/javascript-identifiers

## parsing props from one file to another

specifically, parsing an event handler

Talker.js
```javascript
import React from 'react';
import ReactDOM from 'react-dom';
import { Button } from './Button';

class Talker extends React.Component {
  talk() {
    let speech = '';
    for (let i = 0; i < 10000; i++) {
      speech += 'blah ';
    }
    alert(speech);
  }
  
  render() {
    return <Button talk={this.talk} />;
  }
}

ReactDOM.render(
  <Talker />,
  document.getElementById('app')
);
```

Button.js
```javascript
import React from 'react';

export class Button extends React.Component {
  render() {
    return (
      <button onClick={this.props.talk}>
        Click me!
      </button>
    );
  }
}
```

## this.props.children

```javascript
import React from 'react';

export class List extends React.Component {
  render() {
    let titleText = `Favorite ${this.props.type}`;
    if (this.props.children instanceof Array) {
    	titleText += 's';
    }
    return (
      <div>
        <h1>{titleText}</h1>
        <ul>{this.props.children}</ul>
      </div>
    );
  }
}
```

## defaultProps
```javascript
import React from 'react';
import ReactDOM from 'react-dom';

class Button extends React.Component {
  render() {
    return (
      <button>
        {this.props.text}
      </button>
    );
  }
}

// defaultProps goes here:
Button.defaultProps = {text: 'I am a button'}

ReactDOM.render(
  <Button text = "" />, 
  document.getElementById('app')
);
```

## this.state

https://hacks.mozilla.org/2015/07/es6-in-depth-classes/

http://exploringjs.com/es6/ch_classes.html

```javascript
import React from 'react';
import ReactDOM from 'react-dom';

class App extends React.Component {
	// constructor method begins here:
	constructor(props) {
    super(props);
    this.state = {title : 'Best App'};
  }
	
  render() {
    return (
      <h1>
        Wow this entire app is just an h1.
      </h1>
    );
  }
}
```

```javascript
import React from 'react';
import ReactDOM from 'react-dom';

class App extends React.Component {
	// constructor method begins here:
	constructor(props) {
    super(props);
    this.state = {title : 'Best App'};
  }
	
  render() {
    return (
      <h1>
        {this.state.title}
      </h1>
    );
  }
}

ReactDOM.render(
	<App />,
  document.getElementById('app')
);
```

https://reactjs.org/docs/handling-events.html

```javascript
import React from 'react';
import ReactDOM from 'react-dom';

const green = '#39D1B4';
const yellow = '#FFD712';

class Toggle extends React.Component {
  constructor(props) {
    super(props);
    this.state = {color: green}
    this.changeColor = this.changeColor.bind(this);
  }
  
	changeColor() {
    const newColor = this.state.color == green ? yellow : green;
    this.setState({ color: newColor });
  }
  
  render() {
    return (
      <div style={{background: this.state.color}}>
        <h1>
          Change my color
        </h1>
        <button onClick={this.changeColor}>
          Change color
        </button>
      </div>
    );
  }
}

ReactDOM.render(
	<Toggle />,
  document.getElementById('app')
);
```