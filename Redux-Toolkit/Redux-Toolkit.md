# State Management made easy - Redux Toolkit

Before redux, a long(?) time ago, it's been said that managing state in a React application was a big pain in the a**. 

How do we pass around a state value from component to component. Let's say that we have three components: A, B and C. A is the parent component of both B and C. If we want to pass a state value from B to C, we would first have to send the state from B to A. Then we can pass it down from A to C. Now, managing state in a project where there aren't many components is not that difficult. However, imagine your application size growing. The amount ot UI components will increase too. This will make passing props from one component to another cumbersome.

![haha](haha.PNG)

To solve this, **REDUX** was created. Simply stated, Redux is a state management library for Javascript apps like React. In their official website, they say that Redux can

>help you write applications that behave consistently, run in different environments (client, server, and native), and are easy to test. On top of that, it provides a great developer experience...
