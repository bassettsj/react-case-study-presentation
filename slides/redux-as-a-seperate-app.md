###### Using redux in new "apps"

```js
// App an non-backbone responder to the initialize
// Add redux store for data with adapter for backbone
let _initialized = false;
let _injector;
let _njs;
let _appContext;

class GettingStartedApp extends Component {
    render() {...}
}

class GettingStartedRoot extends Component {
    render() {
        return (
            <Router history={this.props.history}>
                <Route path='/' component={GettingStartedApp}>
                    ...
                </Route>
            </Router>
        );
    }
}

export function init(injector) {
    if (_initialized) {
        return;
    }
    _injector = injector;
    const urlSyncer = _injector.getInstance('urlSyncer');
    urlSyncer.dispose();
    const njs = injector.getInstance('njs');
    _appContext = _injector.getInstance('appContext');
    render(<GettingStartedRoot history={njs.history}/>, document.querySelector('[data-app-buffered]'));
    _initialized = true;
}
```
