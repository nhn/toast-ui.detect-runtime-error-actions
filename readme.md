# TOAST UI Detect Runtime Error Actions

> 🍞🕵️‍♂️ Detect Runtime Error with browserstack

[![GitHub release](https://img.shields.io/github/release/nhn/toast-ui.detect-runtime-error-actions.svg)](https://github.com/nhn/toast-ui.detect-runtime-error-actions/releases/latest) [![GitHub license](https://img.shields.io/github/license/nhn/tui.chart.svg)](https://github.com/nhn/tui.chart/blob/master/LICENSE) [![PRs welcome](https://img.shields.io/badge/PRs-welcome-ff69b4.svg)](https://github.com/nhn/tui.chart/pulls) [![code with hearth by NHN](https://img.shields.io/badge/%3C%2F%3E%20with%20%E2%99%A5%20by-NHN-ff1414.svg)](https://github.com/nhn)

## 💾 How to use

### Setting

1. Add a global variable to the page you want to test. (If you use `tuidoc`, you don't need to add a variable.) Remember the variable name used here!

```js
var errorLogs = [];
window.onerror = function (o, r, e, n) {
  errorLogs.push({ message: o, source: r, lineno: e, colno: n });
};
```

2. Get a token from [browserstack](https://www.browserstack.com/)
3. Register the token in the github secret

### Register action

```yml
- name: detect runtime error
  uses: nhn/toast-ui.detect-runtime-error-actions@master
  with:
    global-error-log-variable: 'errorLogs' # Global variable name specified above
    urls: 'http://nhn.github.io/tui.image-editor/latest/examples/example01-includeUi.html, http://nhn.github.io/tui.image-editor/latest/examples/example02-useApiDirect.html' # List the urls you want to test with,
    browserlist: 'ie8, ie9, ie10, ie11, edge, safari, firefox, chrome' # List the browser you want to test with,
  env:
    BROWSERSTACK_USERNAME: ${{secrets.BROWSERSTACK_USERNAME}} # browserstack username
    BROWSERSTACK_ACCESS_KEY: ${{secrets.BROWSERSTACK_ACCESS_KEY}} # browserstack accesskey
```

## 🍞 TOAST UI Family

- [TOAST UI Chart](https://github.com/nhn/tui.chart)
- [TOAST UI Editor](https://github.com/nhn/tui.editor)
- [TOAST UI Grid](https://github.com/nhn/tui.grid)
- [TOAST UI Calendar](https://github.com/nhn/tui.calendar)
- [TOAST UI Image-Editor](https://github.com/nhn/tui.image-editor)
- [TOAST UI Components](https://github.com/nhn)

## 📜 License

This software is licensed under the [MIT](https://github.com/nhn/tui.chart/blob/master/LICENSE) © [NHN](https://github.com/nhn).
