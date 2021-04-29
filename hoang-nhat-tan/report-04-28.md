# Stage management Week 3 + 4

**React context**

- Context is designed to share data that can be considered "global" for a tree of React components.
- Using context, we can avoid passing props intermediate elements

*Example*
```js
const ThemeContext = React.createContext('light'); //Create Context element

class App extends React.Component{
	render(){
		return(
			<ThemeContext.Provider value='dark'> //Create Provider
				<Toolbar/>
			</ThemeContext.Provider>
		)
	}
}
```

**Flux Architecture**

- Flux is an architecture for building client-side web applications
- Unidirectional data flow: Updating views flow in a single direction
- It suggests to split the application into the following parts:
	- Stores
	- Dispatcher
	- Views
	- Actions/Action Creators

**Redux**

- Redux is a library for managing global application state
	- Redux is typically used with the React-Redux library for integrating Redux and React together.
- Redux uses a "one-way data flow" app structure
	- State describes the condition of the app at a point in time, and UI rendeers based on that state
	- When something happens in the app
		- The UI dispatches an action
		- The store runs the reducers, and the state is updated based on what occurred
		- The store notifies the UI that the state has changed
	- The UI re-renders based on the new state
- Redux uses several types of code
	- Actions are plain objects with a type field, and describe "what happened" in the app
	- Reducers are functions that calculate a new state value based on previos state 
	- A redux store runs the root reducer whenerver an action is dispatched

- Workflow: 
![alt text](https://viblo.asia/uploads/d3e12c8e-7b0b-4874-a119-1eaaf24ea165.png)

- Terminologies: 
	- Slice contains the reducer logic and actions related to specific feature
	- Reducer: How State changes
	- Store: manages state, allow access State via getState(), update State by dispatch(action), regist listener by subcribe(listener)
	- View: display data from Store