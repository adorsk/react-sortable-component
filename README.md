# React Sortable Component

A simple sortable component for ReactJS.

## Installation

```bash
npm install --save react-sortable-component
```

## Usage

### JS

```js
var {SortableItems, SortableItem} = require('react-sortable-component');
...
getInitialState: function () {
    return {
      items: [
        {src: 'http://lorempixel.com/400/400/sports/1'},
        {src: 'http://lorempixel.com/400/400/sports/2'},
        {src: 'http://lorempixel.com/400/400/sports/3'},
        {src: 'http://lorempixel.com/400/400/sports/4'},
        {src: 'http://lorempixel.com/400/400/sports/5'},
        {src: 'http://lorempixel.com/400/400/sports/6'},
        {src: 'http://lorempixel.com/400/400/sports/7'}
      ]
    };
  },
  handleSort: function (items) {
    this.setState({
      items: items
    });
  },
  render: function () {
    var items = this.state.items.map(function (item) {
      return (
        <SortableItem key={item.src} className='sort-sample-item'>
          <LazySizes className='point-events-none' dataSrc={item.src}
            width='126'
            height='126'/>
        </SortableItem>
      );
    });
    return (
      <div>
        <SortableItems className='sort-sample-items' items={this.state.items}
          onSort={this.handleSort}>
          {items}
        </SortableItems>
      </div>
    );
  }

```

### CSS

**Webpack:**

```js
require('react-sortable-component/lib/sortable.css');
```

**Without Webpack:**

```html
<link rel="stylesheet" type="text/css" href="path/to/react-sortable-component/lib/sortable.css">
```

**or appy your style:**

```css
[draggable] {
  -moz-user-select: none;
  -webkit-user-select: none;
  -ms-user-select: none;
      user-select: none;
  -webkit-user-drag: element;
}

.sortable-items:before,
.sortable-items:after {
  content: " ";
  display: table;
}

.sortable-items:after {
  clear: both;
}

.sortable-item {
  height: 150px;
  width: 150px;
  padding: 10px;
  border-radius: 5px;
  float: left;
  margin-left: 10px;
  text-align: center;
  border: 2px solid #000;
  background-color: #eee;
  cursor: move;
}

.sortable-item .point-events-none {
  pointer-events: none;
}

.sortable-item-over {
  border: 2px dashed #000;
}
```

## Props

### SortableItems

| Name | Type | Required | Default | Description |
|------|------|----------|---------|-------------|
| childrent | node | true | | List of SortableItem |
| items | array | false | | List item need sort. |
| onSort | func(arg) | false | | Callback when items sorted. If `items` prop is defined then `arg` is sorted items else `arg` is list index of sorted items. |
| className | string | false | | Your custom class name. |

### SortableItem

| Name | Type | Required | Default | Description |
|------|------|----------|---------|-------------|
| childrent | node | true | | Sortable item content. |
| draggable | bool | false | true | |
| className | string | false | | Your custom class name. |

## Example

View [demo](http://vn38minhtran.github.io/react-sortable-component) or example folder.