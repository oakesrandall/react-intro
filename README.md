![GALOGO](https://camo.githubusercontent.com/6ce15b81c1f06d716d753a61f5db22375fa684da/68747470733a2f2f67612d646173682e73332e616d617a6f6e6177732e636f6d2f70726f64756374696f6e2f6173736574732f6c6f676f2d39663838616536633963333837313639306533333238306663663535376633332e706e67) 

# Intro to React.js: Part 1


Finally! React is here!

### Why is this important?
*This workshop is important because:*

React is another solution to some of our front-end woes. It is a JavaScript *library* (not a framework) that allows us to reframe our pages in terms of the **components** that make it up. React provides a declarative library that keeps the DOM (the view) in sync with your data (the model). It is concerned only with the **V** in **MVC** (unlike Angular, which is MVC for the frontend) and as a result can be used in conjunction with other libraries to help manage state.



### What are the objectives?
<!-- specific/measurable goal for students to achieve -->
*After this workshop, developers will be able to:*


* Explain what ReactJS is and where it fits in our applications' stack.
* Explain the component model of web development.
* Create and render React components in the browser.



## What is ReactJS?

React is a library used to craft modern day UI and create views for the front-end in web, client and native applications.

> **Selling Point:** By modeling small compatible components that focus on just rendering a view, we as developers can move business logic out of the DOM, and therefore improve our app's performance, maintainability, modularity, and readability.

### Some History

The first thing most people hear about React is "Facebook uses it."
* First used by Facebook in 2011. Then Instagram in 2012.
* Went open source in May 2013.

React was born out of Facebook's frustration with the traditional MVC model and how...
  * Re-rendering one thing meant re-rendering much of the page.
  * That had negative implications on processing power and ultimately user experience, which at times became glitchy and laggy.

> If you want to get a taste of what React's all about, [here's an introduction from React.js Conf 2015](https://www.youtube.com/watch?v=KVZ-P-ZI6W4&feature=youtu.be&t=510). Recommend starting around the 8:35 mark and watching until 16:30.

### React in MVC

React's role is to use data to render a UI. This means that React can also coexist with other Javascript frameworks - including Angular! Let them handle the models and controllers, and have React sort out the views.

If you're interested in exactly HOW Angular compares to React, [this article](https://www.quora.com/profile/Pete-Hunt/Posts/Facebooks-React-vs-AngularJS-A-Closer-Look) is a good place to start. To distill it to a couple bullet points:

- Angular is a **framework** that handles the entire frontend MVC. It scales incredibly well assuming there are no other changes to your tech stack. It is huge, powerful, and complex - it requires additional languages (Typescript) and has several new concepts (modules, controllers, scopes, and directives, etc) to learn.
- React is a **library** written entirely in native JS with a JSX compiler, with only two main concepts (components and state). Focused mainly on the user interface, it creates reusable UI components that are fast and smooth. It's simple, and accomodates extensive alterations to your stack.
- Combining React AND Angular will either turn out like [this](http://images5.fanpop.com/image/photos/24500000/Dark-Claw-amalgam-comics-24570126-1024-768.jpg) or like [this](https://s-media-cache-ak0.pinimg.com/originals/d7/67/2a/d7672a682d24c8f3f9ed29e3233b7449.jpg).

## Initial Setup

In order to create a new project and to get our development environment setup, we are going to use the Terminal command `create-react-app`. It will create a new folder in your current directory for the in-class application. Here's an example of the setup commands:

```bash 
$ cd react-intro
$ npm i -g create-react-app
$ create-react-app react-sample-app
$ cd react-sample-app
$ subl .
```

**Explore the app:** Open the new scaffolded application and write down 3 observations and one question you have about the files that you find!

Once you're ready to run the server:

```bash
$ npm run start
```

After running `$ npm run start`, we can view the app at `http://localhost:3000`

`create-react-app` provides us with all the necessary tools and configuration necessary to start writing React. `npm run start` refers to an included script that starts up the development server.

Along with installing the necessary dependencies such as React, ReactDom, Babel and Webpack, it creates a initial app skeleton that looks like this...

```bash
├──README.md
├──  favicon.ico
├──  index.html
├──  node_modules
├──  package.json
└──  src
    ├──  App.css
    ├──  App.js
    ├──  index.css
    ├──  index.js
    └──  logo.svg
```

Most of the important files and primarily where you'll be working in the `/src` directory.

If you want to try creating a react app, go ahead and follow the steps above and investigate the code in the `/src/App.js`, `/src/index.js` and `index.html` files.



## Components

One of the comments made about react when it was first open sourced was that it was "rethinking established best practices". At the time, devs were used to an MVC approach for separation of concerns. In React, we want to move towards more of a component based separation of concerns. On Facebook, you could think of each status post as a mini-component in react. A list  updates is a component that contains several of those mini-components. You could take that one step further and think of the Facebook app as one giant component with several components within it. (Things like the list of status updates, the friends list, the header, etc...)

### You Do: Identifying Components


Break into pairs and take a look at CraigsList. Identify the visual "components" the website is comprised of. We suggest using markers to draw these out on your table! So something like this...

![Component diagram](http://maketea.co.uk/images/2014-03-05-robust-web-apps-with-react-part-1/wireframe_deconstructed.png)

As you're drawing this out, think about the following questions...
* Where do you see "nested components"? Where do you not?
* Are there any components that share the same structure?
* Of these similar components, what is different about them?

Take a picture of your work and Slack it to the classroom channel before the exercise is over.


### Hello World - A Very Basic Component

> No need to follow along with this Hello World example. You will have the chance to implement this yourself.

The basic unit you'll be working with in ReactJS is a **component**.

* Components can be thought of as functional elements that takes in data and as a result produce a dynamic UI.

Throughout class we have separated HTML, CSS and Javascript.

* With components, the lines among those three become a bit blurry.

* Instead, we organize our web apps according to small, reusable components that define their own content, presentation and behavior.

What does a component look like? Let's start with a simple "Hello World" example...

To start, in our `/src/App.js` file, let's remove the contents and in its place add this component definition...

```js
// bring in React and Component instance from react
import React, {Component} from 'react'

// define our Hello component
class Hello extends Component {
  // what should the component render
  render () {
    // Make sure to return some UI
    return (
      <h1>Hello World!</h1>
    )
  }
}

export default Hello
```

Ok let's recap what's going on.

#### What's that HTML doing in my Javascript?

Often times we write out React components in **JSX**.
* JSX is [an alternate Javascript syntax](http://blog.yld.io/2015/06/10/getting-started-with-react-and-node-js/#.V8eDk5MrJPN) that allows us to write code that strongly resembles HTML. It is eventually transpiled to lightweight JavaScript objects.
>Note - this might be a good time to search for a Sublime package called 'JSX', to provide proper syntax highlighting in your documents.

* React then uses these objects to build out a "Virtual DOM" (more on that soon).

> React can be written without JSX. If you want to learn more, [check out this blog post](http://jamesknelson.com/learn-raw-react-no-jsx-flux-es6-webpack/).  

Let's break down the things we see here...

```js
// bring in React and Component instance from react
import React, {Component} from 'react'

// define our Hello component
class Hello extends Component {
  // what should the component render
  render () {
    // Make sure to return some UI
    return (
      <h1>Hello World!</h1>
    )
  }
}

export default Hello
```

##### `class Hello`
This is the component we're creating. In this example, we are creating a "Hello" component.

##### `extends Component`
This is the React library class we inherit from to create our component definition.

##### `render()`
Every component has, at minimum, a render method. It generates a **Virtual DOM** node that will be added to the actual DOM.
* Looks just like a regular ol' DOM node, but it's not yet attached to the DOM.

##### `export default Hello`
This exposes the Hello class to other files which import from the App.js file. The `default` keyword means that any import that's name doesn't match a named export will default to this. Only one default is allowed per file.

**Virtual DOM? How is that different from the usual DOM?**

The Virtual DOM is a Javascript representation of the actual DOM.

* Because of that, React can keep track of changes in the actual DOM by comparing different instances of the Virtual DOM.
* React then isolates the changes between old and new instances of the Virtual DOM and then only updates the actual DOM with the necessary changes.
* By only making the "necessary changes," as opposed to re-rendering an entire view altogether, we save up on processing power.
* This is not unlike Git, with which you compare the difference -- or `diff` -- between two commits.

![Virtual DOM Diagram](https://docs.google.com/drawings/d/11ugBTwDkqn6p2n5Fkps1p3Elp8ZToIRzXzvM4LJMYaU/pub?w=543&h=229)

> If you're interested in learning more about the Virtual DOM, [check this video out](https://www.youtube.com/watch?v=-DX3vJiqxm4).

So we've created the template for our component. Now let's use `/src/index.js` to load in our new component and render it on the DOM. change the third import to import `Hello` instead of App. Also change the `<App />` tag to `<Hello />`...

```js
import React from 'react'
import ReactDOM from 'react-dom'
import Hello from './App.js'

ReactDOM.render(
  <Hello />,
  document.getElementById('root')
)
```

> In place of `ReactDOM.render` some tutorials will use React.renderComponent, which has been phased out. Change outlined [here](http://bit.ly/1E81Whs).

`ReactDOM.render` takes the Virtual DOM node created by `extends Component` and adds it to the actual DOM. It takes two arguments...
  1. The component.
  2. The DOM element we want to append it to.

What language is `<Hello />` written in? **JSX.**

* Similar to XML.
* When we say `<Hello />`, in plain Javascript we are actually saying `React.DOM.div( null, "Hello world.")`
* Basically, a string of React methods that create a virtual DOM node.

> **NOTE:** Whenever you use a self-closing tag in JSX, you **MUST** end it with a `/` like `<Hello />` in the above example.



## Adjust your component

Make your component have a header, a paragraph, and an image. You may build it wrong and get a look at some super helpful React errors! Try to debug on your own, but there is a hint below:

<details>
  <summary><strong>Hint:</strong></summary>

  Your component must have one parent element. That is, you must have one "root" or top level HTML element that holds all of the rest of the HTML that defines your component.

</details>

## Closing

So far, we've learned what React is, what the virtual DOM is in React, and made our first React component (yay!). It's time for a break - in React Intro part 2, we will move on to understand two very essential React topics: `props` and `state`.  
