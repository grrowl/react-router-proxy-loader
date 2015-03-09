react-router-proxy-loader
=========================

Based on [react-proxy-loader](https://github.com/webpack/react-proxy-loader), adapted for `react-router` route handlers.

## Installation

`npm install react-router-proxy-loader`

## Dependencies

Which version to use depends on your version of `react-router`

| react-router     | react-router-proxy-loader |
| ---------------- | ------------------------- |
| 0.11.x and below | 0.1.x                     |
| 0.12.x and above | 0.2.x                     |


## Usage

[Documentation: Using loaders](http://webpack.github.io/docs/using-loaders.html)

Use when requiring the `handler` for a `Route`, and the component will only be loaded when the route is rendered.

```js
<Route name="user" handler={require('react-router-proxy!./User.jsx')} />
```

Note that `willTransitionTo` and `willTransitionFrom` will still be called on the dynamically-loaded component.


### Named chunks (0.2.1 and above)

If you have nested or sibling Routes that you want to be loaded together, you can name the components using `?name=chunkName`

```js
<Route name="user" handler={require('react-router-proxy!./User.jsx?name=user')}>
    <Route name="details" handler={require('react-router-proxy!./UserDetails.jsx?name=user')}>
    <Route name="settings" handler={require('react-router-proxy!./UserSettings.jsx?name=user')}>
    <Route name="other" handler={require('react-router-proxy!./UserOther.jsx?name=user')}>
</Route>
```

This will cause the `user` chunk to be loaded if any of the three user pages is loaded.  It will also mean that you won't need two separate calls for the base class and child class.


# License

MIT (http://www.opensource.org/licenses/mit-license.php)