# React Native useRef Async Update Error

This repository demonstrates a common error in React Native when using `useRef`. The `current` property of a ref is not immediately available after the component mounts, leading to errors if accessed synchronously during the initial render.

## Bug Description
The bug occurs because `myRef.current.measure` is called within the `useEffect` hook's dependency array, which executes immediately after the component mounts. However, the `current` property of `myRef` might not yet be populated, resulting in a `Cannot read properties of undefined (reading 'measure')` error.

## Solution
The solution involves checking if `myRef.current` is defined before accessing its properties or using a callback that is executed after the ref has been updated. This ensures the code doesn't try to access the ref's properties before they are available.

## How to Reproduce
1. Clone the repository.
2. Run `npm install`.
3. Run `npx react-native run-android` (or iOS equivalent).