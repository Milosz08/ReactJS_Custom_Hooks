## Custom useful React hooks

In this repository I store useful custom hooks in React. If you want to use one of these, you will find a short
documentation below. Hooks written with TypeScript.

### Hooks:

---

* `useMultipleRef()` - this is an improved useRef hook that allows you to create multiple references with a function.
Passing count of referential elements to will be created by hook and returned object with referential objects
array and function returned all currents of this referential's in separate array.

Sample usage:
```tsx
import * as React from 'react';

const SampleComponent: React.FC = (): JSX.Element => {
    
    const { elRefs, getCurrents } = useMultipleRefs(3);
    const [ firstChild, secondChild, thirdChild ] = elRefs;
    
    useEffect(() => {
        if (elRefs) console.log(getCurrents());
    }, [ getCurrents ]);
    
    return (
        <div class = 'container'>
            <div class = 'children' ref = {firstChild} />
            <div class = 'children' ref = {secondChild} />
            <div class = 'children' ref = {thirdChild} />
        </div>
    );    
};
```
---
* `useDidMount()` - this hook maybe used to check if it is the first rendering of a component or one of the others (very 
useful for animations). Returns the boolean value representing count of component renderer (true - first, false – second 
and subsequent).

Sample usage:
```tsx
import * as React from 'react';

const SampleComponent: React.FC = (): JSX.Element => {
    
    const isMount = useDidMount();
    
    useEffect(() => {
        if (isMount) console.log('I am mounted first time!');
        else console.log('This is my next mounting!');
    }, []);
    
    return (
        <div class = 'container'>
            <div class = 'children' ref = {firstChild} />
            <div class = 'children' ref = {secondChild} />
            <div class = 'children' ref = {thirdChild} />
        </div>
    );    
};
```
---