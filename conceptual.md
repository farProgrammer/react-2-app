### Conceptual Exercise

Answer the following questions below:

- What is the purpose of the React Router?
A: React Router is a library that allows us to do client-side routing. It's possible to achieve client-side routing without it, but React Router offers some benefits that are a lot of work to achieve without it. With React Router, our "browsing history" is tracked, which allows us to move forward and backwards through "pages" viewed and to bookmark "pages".

- What is a single page application?
A: An SPA is an app that uses only client-side routing to display content.

 The content is changed out in a way that is similar to the set-changing work that happens between scenes during a play. Same stage, but new props and backdrop. The URL updates as we click on links, even though there is no request to a server taking place.

- What are some differences between client-side and server-side routing?
A: With client-side routing, all of the content is already available to us, and we just switch out what we are showing without page refreshes and without making any requests to a server.  With client-side still have the ability to do things like:

  * go back to last page, and React will remember (is cache the right term here?) the page you were on
  * bookmark a page or send a URL to a specific page to another person

- What are two ways of handling redirects with React Router? When would you use each?
A: The two ways of handling redirects are to render a Redirect component or use the useHistory hook. The main difference between these two methods is that useHistory accesses the window.history object and lets us push new paths onto it, which enables the use of the back and forwards arrow buttons.

So, we use the useHistory hook when we need that 'back' and 'forwards' capability. It is typically used when a user submits a form to create content or logs in or performs some other action where there is a logical place to redirect them to based on that action. A good use case for the Redirect component is when the user tries to access a path (either intentionally or unintentionally because of a typo in the URL path) which has not been defined or a path with content they are not authorized to view.

- What are two different ways to handle page-not-found user experiences using React Router? 
A: One way is to design a component that renders when no route matches the URL. This would mimic the 404 page experience with server-side routing. Another way is to use a Redirect component to send the user to the path they most likely wanted.

- How do you grab URL parameters from within a component using React Router?
A: When specifying a path using a Route component inside of a BrowserRouter component, we write the parameter part of the URl preceded by a colon (':'), e.g., path="/animals/:animal". Let's say the Route component has a child Animal component. Inside the file containing the code for the Animal component, we call the useParams hook that comes with React Router. useParams will figure out what the param(s) are for the Animal component by looking at the URL that renders it. It can see that the key is (in this case) 'animal' and the value is, say, 'zebra' if that's the value we used (e.g., "/animals/zebra").

- What is context in React? When would you use it?
A: Context is a React API that gives us access to data across a specified component hierarchy. That hierarchy can encompass the whole application if we want it to. Context solves the problem of prop drilling down numerous levels of an app, because it allows us to make props accessible to many levels of components. Common use cases for context include making the following types of data accessible to many (or all) levels of components:
  * user language preferences
  * user preference for light or dark display mode
  * who is the currently logged-in user


- Describe some differences between class-based components and function
  components in React.
A: Some differences between class-based components and functional components are as follows:
  * The main difference is that class-based components cannot use the very convenient hooks that functional components can use.
  * In a class-based component, there is a single piece of state. It is an object, and it contains all of the state for the component. In functional components, we can have multiple pieces of state that can be updated separately.
  * Class-based components inherit many methods from React.Component. Similar functionality in functional components comes from importing hooks.
  

- What are some of the problems that hooks were designed to solve?
A: Class-based components are fraught with problems and inconveniences. They work, but functional components are much nicer, because they can use hooks to solve a lot of the problems with class-based components. 

Problems hooks were designed to solve:
1. **Event handlers and instance methods don't naturally play nicely together.**  setState works fine when used in a callback function for an event handler on an element, but doing it this way is not ideal, because a new function will be created every time the component is rendered. However, if we try to pull that function out into an instance method and call it in the event handler using `this.methodName`, we run into another problem. In the event handler, we lose the context of `this` _unless_ we fix this problem in the constructor by binding the value of `this` (referring to an instance of the component) to a copy of that instance method. Then, we call the bound method in the event handler. This approach is complicated and clunky, but it's necessary with class components.

2. **With class components, there are a lot of lifecycle methods, and they all run at different times in the component lifecycle.** In a functional component, there is a single hook (useEffect) that can serve the same purpose as all of the lifecycle methods.

3. **There is no good way to share code/logic between lifecycle methods on a component.** Hooks take care of this in functional components.

4. **There is no good way to share logic/functionality among class components.** Class components rely on `this.state` and `this.props`, and those can't be moved into a separate function easily.

5. **Putting all pieces of state in one place (as in a class-based component) is clunky.** It also means that we have to be very careful with how we name the pieces of state. The names should be universal enough to work with many use cases, but not so abstract as to be confusing.With the useState hook, we can have many pieces of state and update them separately, which allows for more flexibility and modularity.