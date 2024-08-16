# React Context Tutorial

This project demonstrates the usage of React Context for state management across components without prop drilling.

## Components

1. `ContextTutorial`: The main component that provides the context.
2. `Login`: A component with an input field to update the username.
3. `User`: A component that displays the current username.

## Key Concepts

- [React Context](https://react.dev/reference/react/createContext): For sharing data between components without explicit prop passing.
- [useState Hook](https://react.dev/reference/react/useState): For adding state to functional components.
- [useContext Hook](https://react.dev/reference/react/useContext): For consuming context in child components.

## Operations

1. **ContextTutorial Component Mount**:
   - Initializes `username` state with an empty string.
   - Wraps child components with `AppContext.Provider`.

2. **Login Component Mount**:
   - Accesses `setUsername` function from AppContext.
   - Renders an input field for username entry.

3. **User Component Mount**:
   - Accesses `username` value from AppContext.
   - Displays the current username.

4. **User Input in Login Component**:
   - `onChange` event triggers `setUsername`.
   - Updates `username` state in ContextTutorial.

5. **State Update in ContextTutorial**:
   - `AppContext.Provider` value updates.
   - Triggers re-render of Login and User components.

6. **User Component Re-render**:
   - Displays updated username value.

## Usage

To use this example:

1. Clone the repository.
2. Install dependencies with `npm install`.
3. Run the app with `npm start`.

## Further Reading

- [React Documentation](https://react.dev/learn)
- [Using the Context API in React](https://react.dev/learn/passing-data-deeply-with-context)
- [Hooks API Reference](https://react.dev/reference/react)

