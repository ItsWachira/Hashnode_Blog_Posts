## ReactJS: A complete beginner's guide on learning Reactjs.

## Overview.
If you want to learn  React, but you still aren't sure. You still have some questions, such as:

- How should I create my React projects?
- What tools should I have to build my React app?
- Do I need to learn JavaScript first before learning React?


If you're looking for answers to any of these questions (and more), then be sure to dive in.😊👨‍💻 This guide will cover the major essential areas you need to know to begin learning react by being as objective as possible. Hey, I am still learning it, and I will be happy to share my honest opinion on my journey so far.😊👨‍💻

**Note: The official technical documentation for any tool/technology is an essential resource to use to learn the technicalities of the tool.**

For this case, I highly recommend visiting **[react's official documentation](https://reactjs.org/tutorial/tutorial.html).**


> Let's get started...


# Introduction
## What is React?
React or React JS is a JavaScript front-end library built by Meta which lets you create an HTML-based GUI. It makes the task easier by providing a component-based architecture that was only available to languages like Java and C# before.

There are a good number of frontend frameworks used by developers globally to build beautiful and engaging client-side UI. They include:

- Angularjs

- Vuejs

- Reactjs

- Svelte

- Ember.

React however tops the charts in terms of usage, popularity, and community size. 
According to the latest survey by [ StackOverflow](https://survey.stackoverflow.co/2022/#section-most-loved-dreaded-and-wanted-web-frameworks-and-technologies) on developer tools: 

Reactjs seconds nodejs on the list of the most commonly used web frameworks by professional developers. However, bearing in mind that Nodejs supports expressjs for building backend services, we can conclude that Reactjs is the most popular front-end framework.

See the image below.

![react.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1661864358941/yAQ9DmDZD.jpg align="left")

## Benefits of React in Front-end development

- **Intuitive**

ReactJS is extremely intuitive to work with and provides interactivity to the layout of any UI. It enables fast and quality-assured application development that in turn saves time for both clients and developers.

- **Provides Reusable Components**

ReactJS provides reusable components that developers have the authority to reuse and create a new application. Reusability is a life-saver remedy for developers. This platform gives the developers the authority to reuse the components build for some other application having the same functionality. Thereby, reducing the development effort and ensuring a flawless performance.

**- SEO-friendly**

React JS was introduced after immense research and improvements by Facebook. It allows developers to build amazing, SEO-friendly user interfaces across browsers and engines.


Further, it has the largest community support, GitHub stars, hiring trends, and usage than other front-end frameworks.
### Github stars stats.

![github stars.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1661865110497/Tp-HvLYt6.jpg align="left")

### Hiring trends

![Screenshot 2022-08-30 161247.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1661865184650/kxkz4EZ73.jpg align="left")

Therefore, learning ReactJS will not only add an essential developer skill to your resume but will also give you a competitive edge in the professional work environment.

## How should I create my React projects?
**Create React App** is an easy command, and reliable way to make a new React project and gives you essential tools and scripts to run, develop, and build your project for deployment.

**Create React App** uses [Babel](https://babeljs.io/) -(Javascript compiler) and Webpack to transpile and bundle your code (in short, to make it possible to run in the browser).

Additionally, it provides great development tools like ESLint to "lint" your code, i.e. it tells you about problems in the code you've written as you write it.

See the code below:  Run the command on your terminal.

```
npx create-react-app my-react-app
``` 
## What tools should I have to build my React app?
To build functional React Apps on your computer, there are a few essential tools you will require:

- Node / NPM (I recommend installing the latest version)

- A good code editor 

- Git (to handle version control and hosting your projects on GitHub)

## Essential React concepts you need to learn.
React has a number of new concepts that give us a new way to think about building applications on the web and in general.

Some of the common concepts include:

### JSX.
JSX stands for JavaScript XML. JSX allows us to put HTML into JavaScript.
It is simply a syntax extension of React. It allows us to directly write HTML in React.

React uses JSX for templating instead of regular JavaScript. It is not necessary to use it, however, the following are the advantages that come with it:

### Components.
Components are independent and reusable bits of code. They serve the same purpose as JavaScript functions, but work in isolation and return HTML. 

Components are grouped into two types, Class components, and Function components. Both types have their specific use cases. If you want to learn more, Check out this [article](https://www.geeksforgeeks.org/reactjs-components/).

### Props and state
**Props** - Props is short for properties and they are used to pass data between React components. In react, the data flow between components is uni-directional.
w is State
 **State** - allows components to create and manage their own data.

Props are used to pass data, whereas state is for managing data. Data from props is read-only, and cannot be modified by a component that is receiving it from outside. State data can be modified by its own component, but is private (cannot be accessed from outside)

###  React Hooks.
Hooks are the new feature introduced in the React 16.8 version. It allows you to use state and other React features without writing a class. Hooks are the functions that "hook into" React state and lifecycle features from function components. It does not work inside classes.

Hooks are backward-compatible, which means it does not contain any breaking changes. Also, it does not replace your knowledge of React concepts.

There are two types:
 - useState.
- useEffect


If you want a comprehensive list of all the major React concepts that I believe are essential in a convenient cheat sheet. You can find it [here](https://www.freecodecamp.org/news/react-cheatsheet-with-real-world-examples/):


Do I need to learn every single React feature/concept?
No, you don't. Focus on the main concepts. I am doing the same.👨‍💻😊

## Do I need to learn JavaScript before React?
React is essentially a JavaScript library that prides itself on being "just JavaScript", if you're going to learn React, you will eventually need to become good at JavaScript as well.

I am personally still learning JavaScript ( there are so many concepts to learn that I don't think any developer could say that they have finished learning a language ). Some developers would argue that it is possible to just "start" with React, then somehow work your way to learning Javascript. 

Does it work? I don't have a precise answer to this. We approach concepts in different ways and it's safe to say learning is by far, relative to each individual. 

Therefore, learning is solely dependent on your choices and preferences.

Nonetheless, the better you become at JavaScript, the better you will become at building things in React. 

## What React libraries should I use?

There are a number of React libraries that can be used within your React projects. Each library has a set of unique functionality.

React is a library, not a framework. Many of the tools that will be required to build your projects are simply not available in React. React does not provide its own solution for writing styles, animating components, managing global app states, or creating routes or pages.

To build any significant React project, you will need to become knowledgeable about various libraries to give you the functionality that you need.

They include: 
- For state management, use Zustand (Redux is still good with Redux Toolkit)
- For styling, use TailwindCSS
- For routing, use React Router (React Location is also promising)
- For data fetching, use React Query
- For forms, use React Hook Form

> The libraries' list above was curated from google research on the most popular libraries to use with react.

---
## Conclusion
This tutorial has covered some of the major concepts any beginner needs to know before starting out with learning react.

I am hoping that this article has given you an ideal picture of what to expect with react. I am still on the same learning journey, and some of the concepts I have mentioned above have helped me a great deal in learning and understanding front-end development with React.

---

Thanks for reading! ❤️ 
 If you want to be the first to see my next article, follow me on [Hashnode](https://itswachira.hashnode.dev/) and on [Twitter](https://twitter.com/WachiraGichuhi)!

















