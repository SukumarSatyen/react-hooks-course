# useCallback Tutorial

## Important concepts

### useState
A Hook that lets you add React state to function components.
- `const [toggle, setToggle] = useState(false);`: Manages the toggle state for showing/hiding an h1 element.
- `const [data, setData] = useState("Yo, pls sub to the channel!");`: Stores a string message used in the returnComment function.

### useCallback
A Hook that lets you cache a function definition between re-renders.
- `const returnComment = useCallback((name) => { return data + name; }, [data]);`: Memoizes the returnComment function, preventing unnecessary re-renders of the Child component unless the 'data' dependency changes.

### useEffect
A Hook that lets you perform side effects in function components.
- `useEffect(() => { console.log("FUNCTION WAS CALLED"); }, [returnComment]);`: Logs a message to the console whenever the returnComment function reference changes, demonstrating when the Child component re-renders.

### Child Component
A component that is nested within another component (the parent component).
- `<Child returnComment={returnComment} />`: Renders the Child component in CallBackTutorial.js, passing the memoized returnComment function as a prop.
- The entire Child.js file defines a child component that receives and uses the returnComment prop.

## Operations

First is the mounting of the CallBackTutorial component. 

Then,
1. CallBackTutorial component starts mounting:
   - React processes the import statements, bringing in necessary dependencies (axios, useState, useCallback, and the Child component).

2. Function component CallBackTutorial is defined and executed:
   - `useState(false)` is called to initialize the `toggle` state:
     - React creates a state variable `toggle` with initial value `false`.
     - React creates a setter function `setToggle`.
   - `useState("Yo, pls sub to the channel!")` is called to initialize the `data` state:
     - React creates a state variable `data` with the initial string value.
     - React creates a setter function `setData`.

3. `useCallback` is executed:
   - React creates a memoized version of the `returnComment` function.
   - The function is memoized with `data` as a dependency, meaning it will only be recreated if `data` changes.

4. The JSX in the return statement of CallBackTutorial is evaluated:
   - React processes the JSX, creating a virtual DOM representation.

5. Child component is encountered in the JSX:
   - React sees `<Child returnComment={returnComment} />`.
   - It prepares to render the Child component, passing the memoized `returnComment` function as a prop.

6. Child component starts rendering:
   - The function component Child is executed with `returnComment` prop.
   - `useEffect` in Child is encountered:
     - React schedules this effect to run after the render is committed to the screen.
   - The JSX in Child's return statement is evaluated:
     - `returnComment("Pedro")` is called, concatenating "Pedro" to the current value of `data`.
     - The result is placed within a `<div>`.

7. React completes the initial render of both components:
   - The virtual DOM is created for the entire component tree.
   - React commits this to the actual DOM, painting the initial UI to the screen.

8. After the render, React runs the scheduled effects:
   - The `useEffect` in Child component is executed.
   - "FUNCTION WAS CALLED" is logged to the console.

9. The application is now in its initial state, waiting for user interaction.

10. User clicks the "Toggle" button:
    - The onClick handler is triggered.
    - `setToggle(!toggle)` is called, scheduling a state update.

11. React processes the state update:
    - It marks the CallBackTutorial component for re-rendering.

12. Re-render of CallBackTutorial begins:
    - The function component is executed again.
    - `useState` and `useCallback` hooks are called again:
      - `toggle` state is updated with its new value.
      - `data` state remains unchanged.
      - `returnComment` function is not recreated as `data` hasn't changed.

13. JSX in CallBackTutorial is re-evaluated:
    - If `toggle` is now `true`, the `<h1> toggle </h1>` element is included in the virtual DOM.

14. Child component is encountered again:
    - React checks if any props have changed.
    - `returnComment` is the same reference as before (thanks to useCallback), so Child is not re-rendered.

15. React completes the re-render:
    - The new virtual DOM is compared with the previous one (diffing process).
    - Only the changes (the toggle h1 element) are applied to the actual DOM.

16. The application is now in its updated state, again waiting for user interaction.

This cycle of user interaction → state update → re-render continues throughout the lifecycle of the application, with Child only re-rendering if the `data` state in CallBackTutorial changes, causing a new reference of `returnComment` to be created.

## React Dev Reference

- useState: https://react.dev/reference/react/useState
- useCallback: https://react.dev/reference/react/useCallback
- useEffect: https://react.dev/reference/react/useEffect
- Components and Props: https://react.dev/learn/your-first-component
