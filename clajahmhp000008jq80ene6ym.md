# How to Start Testing Your React Apps Using the React Testing Library

Testing is often seen as a tedious process. It's extra code you have to write, and in some cases, to be honest, it's not needed. But every developer should know at least the basics of testing. It increases confidence in the products they build, and for most companies, it's a requirement.

 React provides an amazing library called the react-testing-library which helps you test your React Apps more efficiently. You use it with Jest.

In this article, we will see the 8 simple steps you can take to start testing your React Apps like a boss.
## Prerequisites
This tutorial assumes that you have at least a basic understanding of React. I will focus only on the testing part.

## Basics
Terms to note in this article:
- **it or test:** describes the test itself. It takes as parameters the name of the test and a function that holds the tests.

- **expect:** the condition that the test needs to pass. It will compare the received parameter to a matcher.

- **a matcher: **a function that is applied to the expected condition.

- **render:** the method used to render a given component.

## What is the React Testing Library?
The React Testing Library is a very lightweight package created by Kent C. Dodds. It's a replacement for Enzyme and provides light utility functions on top of react-dom and react-dom/test-utils.

The Library is a DOM testing library, which means that instead of dealing with instances of rendered React components, it handles DOM elements and how they behave in front of real users.

It's a great library, it's (relatively) easy to start using, and it encourages good testing practices. Note – you can also use it without Jest.

"The more your tests resemble the way your software is used, the more confidence they can give you."

> You don't need to install any packages since create-react-app comes with the library and its dependencies.

### 1. How to create a test snapshot
A snapshot, as the name suggests, allows us to save the snapshot of a given component. It helps a lot when you update or do some refactoring, and want to get or compare the changes.

Now, let's take a snapshot of the App.js file.
**App.test.js**
```
import React from 'react'
import {render, cleanup} from '@testing-library/react'
import App from './App'

 afterEach(cleanup)
 
 it('should take a snapshot', () => {
    const { asFragment } = render(<App />)
    
    expect(asFragment(<App />)).toMatchSnapshot()
   })
});
```
To take a snapshot, we first have to import render and cleanup. These two methods will be used a lot throughout this article.

render, as you might guess, helps to render a React component. And cleanup is passed as a parameter to afterEach to just clean up everything after each test to avoid memory leaks.

Next, we can render the App component with render and get back asFragment as a returned value from the method. And finally, make sure that the fragment of the App component matches the snapshot.

Now, to run the test, open your terminal and navigate to the root of the project and run the following command:

```
  npm test
``` 
As a result, it will create a new folder __snapshots__ and a file App.test.js.snap in the src which will look like this:

**App.test.js.snap**

```
// Jest Snapshot v1, https://goo.gl/fbAQLP

exports[`Take a snapshot should take a snapshot 1`] = `
<DocumentFragment>
  <div class="App">
    <h1>Testing</h1>
  </div>
</DocumentFragment>
`;
``` 
 If you make another change in App.js, the test will fail because the snapshot will no longer match the condition. To make it passes, just press u to update it. And you'll have the updated snapshot in App.test.js.snap.

Now, let's move on and start testing our elements.

### 2. Testing DOM elements
To test our DOM elements, we first have to look at the TestElements.js file.

**TestElements.js**
```
import React from 'react'

const TestElements = () => {
 const [counter, setCounter] = React.useState(0)
  
 return (
  <>
    <h1 data-testid="counter">{ counter }</h1>
    <button data-testid="button-up" onClick={() => setCounter(counter + 1)}> Up</button>
    <button disabled data-testid="button-down" onClick={() => setCounter(counter - 1)}>Down</button>
 </>
    )
  }
  
export default TestElements
```
Here, the only thing you have to retain is data-testid. It will be used to select these elements from the test file. Now, let's write the unit test:

Test if the counter is equal to 0:

**TestElements.test.js**

```
import React from 'react';
import { render, cleanup } from '@testing-library/react';
import TestElements from './TestElements'

afterEach(cleanup);

  it('should equal to 0', () => {
    const { getByTestId } = render(<TestElements />); 
    expect(getByTestId('counter')).toHaveTextContent(0)
``` 
As you can see, the syntax is quite similar to the previous test. The only difference is that we use getByTestId to select the necessary elements (remember the data-testid) and check if it passed the test. 

Test if the buttons are enabled or disabled:

TestElements.test.js (add the following code block to the file)

```
it('should be enabled', () => {
    const { getByTestId } = render(<TestElements />);
    expect(getByTestId('button-up')).not.toHaveAttribute('disabled')
  });

  it('should be disabled', () => {
    const { getByTestId } = render(<TestElements />); 
    expect(getByTestId('button-down')).toBeDisabled()
  });
``` 
Here, we use getByTestId to select elements and check for the first test if the button has a disabled attribute. And for the second, if the button is disabled or not.

And if you save the file or run it again in your terminal yarn test, the test will pass.

Congrats! Your first test has passed!
### 3. Testing events
Before writing our unit tests, let's first check what TestEvents.js looks like.
**TestEvents.js**
```
import React from 'react'

const TestEvents = () => {
  const [counter, setCounter] = React.useState(0)
  
return (
  <>
    <h1 data-testid="counter">{ counter }</h1>
    <button data-testid="button-up" onClick={() => setCounter(counter + 1)}> Up</button>
    <button data-testid="button-down" onClick={() => setCounter(counter - 1)}>Down</button>
 </>
    )
  }
  
  export default TestEvents
```
Now, let's write the tests.

Test if the counter increments and decrements correctly when we click on buttons:

**TestEvents.test.js**


```
import React from 'react';
import { render, cleanup, fireEvent } from '@testing-library/react';
import TestEvents from './TestEvents'

  afterEach(cleanup);
  
  it('increments counter', () => {
    const { getByTestId } = render(<TestEvents />); 
    
    fireEvent.click(getByTestId('button-up'))

    expect(getByTestId('counter')).toHaveTextContent('1')
  });

  it('decrements counter', () => {
    const { getByTestId } = render(<TestEvents />); 
    
    fireEvent.click(getByTestId('button-down'))

    expect(getByTestId('counter')).toHaveTextContent('-1')
  });


``` 
These two tests are very similar except for the expected text content. The first test fires a click event with fireEvent.click() to check if the counter increments to 1 when the button is clicked. The second one checks if the counter decrements to -1 when the button is clicked. **fireEvent** has several methods you can use to test events, so feel free to dive into the documentation to learn more.

## Wrapping Up
The React Testing Library is a great package for testing React Apps. It gives us access to jest-dom matchers we can use to test our components more efficiently and with good practices. Hopefully, this article was useful, and it will help you build robust React apps in the future.

Thanks for reading it!
