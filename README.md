# Next.js 15 useEffect Cleanup Issue

This repository demonstrates a subtle bug related to the `useEffect` hook in Next.js 15 applications.  The counter on the About page continues incrementing even after navigating away from the page. This is due to an improper cleanup in the `useEffect` hook.

## Bug Description

A counter on the about page should stop counting when navigating to a different page.  However, the counter in this example continues incrementing in the background, even after the component has unmounted.  This is a common mistake when using setInterval in useEffect without proper cleanup.

## How to Reproduce

1. Clone this repository.
2. Run `npm install`.
3. Run `npm run dev`.
4. Navigate to the `/about` page.
5. Navigate away from the `/about` page (e.g., back to the home page).
6. Observe that the counter continues incrementing in the background (you might need to open the developer console and view the counter's value).

## Solution

The solution involves ensuring that the `setInterval` is properly cleared when the component unmounts.  This is achieved by returning a cleanup function from the `useEffect` hook.  See `aboutSolution.js` for a corrected implementation.