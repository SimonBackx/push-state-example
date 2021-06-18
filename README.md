# push-state-example
Demonstration of History API bug in DuckDuckGo's browser for iOS

## Environment

- App version: 7.63.7.0
- Device model: iPhone 12 pro
- iOS version: 14.6

## Steps to reproduce the bug

- Start with a simple website (the initial website) that opens a different website (the opened website) in a new tab when clicking on a link:
```html
<a href="https://example.com" target="_blank">Open in new tab</a>
```
- On the opened website, use the History API's pushState method (e.g. when clicking on a button) to navigate to a new page
```js
history.pushState({ currentPage: "page1" }, "Page 1")
```
- Press the back button in the browser to go to the previous page

## Expected behavior

It should go back to the first page of the opened website.

## Actual behavior

It goes back to the initial website and skips over the first page (or more intermediate pages) on the opened website.

## Example

I've made a small repository with example code and hosted it so you can try it yourself without having to write any code.

- Open the following URL (= the initial website) in DuckDuckGo's browser for iOS:
`https://simonbackx.github.io/push-state-example/open-in-tab.html`
- Click on the link `Open in new tab`
- Hit one or more buttons `Home`, `Page1`, or `Page2`
- Go back using the browser buttons. You'll see that any intermediary pages are skipped

Now compare this with the normal behavior:
- Open the URL of the opened website by entering it directly in DuckDuckGo's browser for iOS, instead of opening it in a new tab using the initial website:
`https://simonbackx.github.io/push-state-example/`
- Hit one or more buttons `Home`, `Page1`, or `Page2`
- Go back using the browser buttons. You'll see that everything works as expected

You can check the source at https://github.com/SimonBackx/push-state-example
