###### Use React Components in Backbone View Classes

```
export default BaseView.extend({
    initialize(options = {}) {
        this.head = options.head || [];
        this.rows = options.rows || [];
        this.sort = options.sort || true;
    },
    render() {
        ReactDOM.render(
            <Table data={ this.mapToData() } sortable= { this.mapToSort() } />,
            this.el
        );

        return this;
    }
});
```
