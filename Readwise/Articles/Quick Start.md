# Quick Start

![rw-book-cover](https://react.dev/images/og-learn.png)

## Metadata
- Author: [[react.dev]]
- Full Title: Quick Start
- Category: #articles
- Summary: This document provides a quick start guide to using React, a JavaScript library for building user interfaces. It covers how to create and nest components, add markup and styles, display data, render conditions and lists, respond to events, update the screen, use hooks, and share data between components using props. The document includes examples of code for each of these topics and provides helpful explanations and tips.
- URL: https://react.dev/learn

## Highlights
- Creating and nesting components
  React apps are made out of *components*. A component is a piece of the UI (user interface) that has its own logic and appearance. A component can be as small as a button, or as large as an entire page.
  React components are JavaScript functions that return markup:
  function MyButton() { return ( <button>I'm a button</button> );}
  Now that you’ve declared `MyButton`, you can nest it into another component:
  export default function MyApp() { return ( <div> <h1>Welcome to my app</h1> <MyButton /> </div> );}
  Notice that `<MyButton />` starts with a capital letter. That’s how you know it’s a React component. React component names must always start with a capital letter, while HTML tags must be lowercase.
  Have a look at the result:
  function MyButton() {
  return (
  <button>
  I'm a button
  </button>
  );
  }
  export default function MyApp() {
  return (
  <div>
  <h1>Welcome to my app</h1>
  <MyButton />
  </div>
  );
  }
  Welcome to my app
  The `export default` keywords specify the main component in the file. If you’re not familiar with some piece of JavaScript syntax, [MDN](https://developer.mozilla.org/en-US/docs/web/javascript/reference/statements/export) and [javascript.info](https://javascript.info/import-export) have great references. ([View Highlight](https://read.readwise.io/read/01hd6v3rwwnwxx1bbxy0j7c3br))
    - Tags: [[react]] 
    - Note: This section is about creating and nesting components in React. React is a tool used to build apps, and those apps are made up of components. A component is like a small piece of the app that has its own look and behavior. You can create a component by writing a special kind of JavaScript function, which returns what the component should look like. Once you’ve created a component, you can use it inside another component, like a button inside a page. When you use a component inside another one, it’s called “nesting.” You can tell that a component is a React component because its name starts with a capital letter. Inside a component, you can use other components, just like you can use HTML tags like `<div>` and `<h1>`. When you put a component inside another one, you use a special syntax that looks like `<ComponentName />`. You can use as many components as you want to create your app.
      React apps are made of components. Components are JavaScript functions that return markup. You can nest components into another component.
- Writing markup with JSX
  The markup syntax you’ve seen above is called *JSX*. It is optional, but most React projects use JSX for its convenience. All of the [tools we recommend for local development](https://react.dev/learn/installation) support JSX out of the box.
  JSX is stricter than HTML. You have to close tags like `<br />`. Your component also can’t return multiple JSX tags. You have to wrap them into a shared parent, like a `<div>...</div>` or an empty `<>...</>` wrapper:
  function AboutPage() { return ( <> <h1>About</h1> <p>Hello there.<br />How do you do?</p> </> );}
  If you have a lot of HTML to port to JSX, you can use an [online converter.](https://transform.tools/html-to-jsx) ([View Highlight](https://read.readwise.io/read/01hd6wdhym9ymy94zspy9jpsqb))
    - Note: JSX is a way to write HTML-like code in JavaScript. It makes coding faster and easier, and most React projects use it. JSX is stricter than HTML, which means you have to pay attention to details like closing tags like `<br />`. Also, you can't return multiple JSX tags, so you have to wrap them into a shared parent tag like `<div>...</div>` or use an empty wrapper `<>...</>` instead. If you have a lot of HTML to convert to JSX, you can use an online converter.
- Adding styles
  In React, you specify a CSS class with `className`. It works the same way as the HTML [`class`](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/class) attribute:
  <img className="avatar" />
  Then you write the CSS rules for it in a separate CSS file:
  /* In your CSS */.avatar { border-radius: 50%;}
  React does not prescribe how you add CSS files. In the simplest case, you’ll add a [`<link>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/link) tag to your HTML. If you use a build tool or a framework, consult its documentation to learn how to add a CSS file to your project. ([View Highlight](https://read.readwise.io/read/01hd6wqbxzvww6smb3rayg6p6c))
    - Note: When you want to change how things look in React, you can use something called "styles". This means you can make things look different depending on what you want. To use styles, you first need to create a "CSS class" with a name. You can do this by writing `className="name"` in your code. Then, you tell React what you want this class to look like by writing CSS rules in a separate file. This will change how things with that class name look on your webpage. Remember that React doesn't tell you how to add CSS files, so you might need to look up how to do it depending on what you're using.
- Displaying data
  JSX lets you put markup into JavaScript. Curly braces let you “escape back” into JavaScript so that you can embed some variable from your code and display it to the user. For example, this will display `user.name`:
  return ( <h1> {user.name} </h1>);
  You can also “escape into JavaScript” from JSX attributes, but you have to use curly braces *instead of* quotes. For example, `className="avatar"` passes the `"avatar"` string as the CSS class, but `src={user.imageUrl}` reads the JavaScript `user.imageUrl` variable value, and then passes that value as the `src` attribute:
  return ( <img className="avatar" src={user.imageUrl} />);
  You can put more complex expressions inside the JSX curly braces too, for example, [string concatenation](https://javascript.info/operators#string-concatenation-with-binary):
  const user = {
  name: 'Hedy Lamarr',
  imageUrl: 'https://i.imgur.com/yXOvdOSs.jpg',
  imageSize: 90,
  };
  export default function Profile() {
  return (
  <>
  <h1>{user.name}</h1>
  <img
  className="avatar"
  src={user.imageUrl}
  alt={'Photo of ' + user.name}
  style={{
  width: user.imageSize,
  height: user.imageSize
  }}
  />
  </>
  );
  }
  In the above example, `style={{}}` is not a special syntax, but a regular `{}` object inside the `style={ }` JSX curly braces. You can use the `style` attribute when your styles depend on JavaScript variables. ([View Highlight](https://read.readwise.io/read/01hd70977y21nz5d6cw3kjwbc2))
- y declaring *even* ([View Highlight](https://read.readwise.io/read/01hm252bsn50nmmfy4p8qxfs2d))
- button, the `count` in `MyA` ([View Highlight](https://read.readwise.io/read/01hm25tap7a29t0d9skkkndrar))
- Then, *pass the state down* from `MyApp` to each `MyButton`, together with the shared click handler. You can pass information to `MyButton` using the JSX curly braces, just like you previously did with built-in tags like `<img>`:
  export default function MyApp() { const [count, setCount] = useState(0); function handleClick() { setCount(count + 1); } return ( <div> <h1>Counters that update together</h1> <MyButton count={count} onClick={handleClick} /> <MyButton count={count} onClick={handleClick} /> </div> );}
  The information you pass down like this is called *props*. Now the `MyApp` component contains the `count` state and the `handleClick` event handler, and *passes both of them down as props* to each of the buttons. ([View Highlight](https://read.readwise.io/read/01hm25wzd1v11fb04dxvmz1cq6))
