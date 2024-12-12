# Firebase onAuthStateChanged Unsubscribe Issue

This repository demonstrates a common issue with Firebase's `onAuthStateChanged` listener: improper unsubscription.  The provided code initially lacked a proper cleanup mechanism, leading to memory leaks and potential unexpected behavior. The solution showcases the correct way to unsubscribe from the listener using the returned unsubscribe function within a useEffect cleanup function.

## Problem

The original `onAuthStateChanged` listener was not unsubscribed when the component unmounted. This meant that the listener continued to run, even after the component was no longer needed. This can result in memory leaks and unexpected behavior.

## Solution

The solution uses React's `useEffect` hook to ensure that the listener is unsubscribed when the component is unmounted.  The `return` statement within the `useEffect` function provides the cleanup function to unsubscribe. This function is guaranteed to run when the component unmounts, preventing resource leaks.