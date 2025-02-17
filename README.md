# react-simple-infinite-loading

>

[![NPM](https://img.shields.io/npm/v/react-simple-infinite-loading.svg)](https://www.npmjs.com/package/react-simple-infinite-loading) [![JavaScript Style Guide](https://img.shields.io/badge/code_style-standard-brightgreen.svg)](https://standardjs.com)

## Why?

I wrote an article about [creating an infinite loading list with React and GraphQL](https://dev.to/yvonnickfrin/create-an-infinite-loading-list-with-react-and-graphql-19hh). Someone pointed out the React implementation of the list was a bit complex. I figure out it was possible to write an abstraction for this particular case. Here it is!

This component aims to stay easy to use. If your use case needs more options I recommend using directly awesome libraries from [Brian Vaughn](https://github.com/bvaughn) listed in dependencies section.

## Install

```bash
npm install --save react-simple-infinite-loading
```

## Usage

```jsx
import React from 'react'

import InfiniteLoadingList from 'react-simple-infinite-loading'

function Example({ items, fetchMore, hasMore }) {
  return (
    <div style={{ width: 300, height: 300 }}>
      <InfiniteLoading
        hasMoreItems={hasMore}
        itemHeight={40}
        loadMoreItems={fetchMore}
      >
        {items.map(item => <div key={item}>{item}</div>)}
      </InfiniteLoading>
    </div>
  )
}
```

## Dependencies

`react-simple-infinite-loading` has only three dependencies:

- [react-window](https://github.com/bvaughn/react-window) is made to display efficiently large lists. It only creates components for the visible elements and reuse nodes.
- [react-window-infinite-loader](https://github.com/bvaughn/react-window-infinite-loader/) is a HOC that loads elements just-in-time as user scrolls down the list
- [react-virtualized-auto-sizer](https://github.com/bvaughn/react-virtualized-auto-sizer/) helps you displaying your list so it fits the space available in its parent container.

## Properties

| property name | required | type     | description                                                                                                                                                                                               |
| ------------- | -------- | -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| children      | yes      | function | The children function should return the jsx for an item of the list. An object is passed as parameter containing `item`, `index`, `style`. _You must pass the style to top-level tag of your item's jsx_. |
| items         | yes      | array    | An array of elements. Any type of elements is accepted.                                                                                                                                                   |
| itemHeight    | yes      | number   | The height of an item. All items should have the same height.                                                                                                                                             |
| hasMoreItems  | no       | boolean  | A boolean that determines if there are still items to load using `loadMoreItems` function.                                                                                                                |
| loadMoreItems | no       | function | A function that will be called each time the list need to load more items.                                                                                                                                |

## License

Apache-2.0 © [frinyvonnick](https://github.com/frinyvonnick)
