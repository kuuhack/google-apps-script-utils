# google-apps-script-utils

[![clasp](https://img.shields.io/badge/built%20with-clasp-4285f4.svg)](https://github.com/google/clasp)
[![Develpment](https://github.com/kuuhack/google-apps-script-utils/actions/workflows/main.yml/badge.svg)](https://github.com/kuuhack/google-apps-script-utils/actions/workflows/main.yml)
[![MIT License](https://img.shields.io/github/license/kuuhack/google-apps-script-utils)](https://github.com/kuuhack/google-apps-script-utils/blob/main/LICENSE)

## Description

This repository has some functions to help with Google Apps Script

## Install

```shell
git clone https://github.com/kuuhack/google-apps-script-utils.git
cd google-apps-script-utils
yarn install
yarn clasp login
yarn clasp create --rootDir ./src/ --title utils
yarn clasp push -f
```

## Functions

### `createObjects`, `createValues`

|     | A    | B   | C         |
| --- | ---- | --- | --------- |
| 1   | name | age | favorite  |
| 2   | hoge | 20  | curry     |
| 3   | fuga | 30  | chocolate |
| 4   | piyo | 40  | coffee    |

```js
const myFunction = () => {
  const sheet = SpreadsheetApp.getActiveSheet()
  const values = sheet.getDataRange().getValues()
  const objects = createObjects(values)

  console.log(objects)
  // [ { name: 'hoge', age: 20, favorite: 'curry' },
  //   { name: 'fuga', age: 30, favorite: 'chocolate' },
  //   { name: 'piyo', age: 40, favorite: 'coffee' } ]

  console.log(objects.filter((object) => object.name === 'fuga')[0])
  // { name: 'fuga', age: 30, favorite: 'chocolate' }

  const newValues = createValues(objects)

  console.log(newValues)
  // [ [ 'name', 'age', 'favorite' ],
  //   [ 'hoge', 20, 'curry' ],
  //   [ 'fuga', 30, 'chocolate' ],
  //   [ 'piyo', 40, 'coffee' ] ]

  console.log(newValues.filter((record) => record.includes('fuga'))[0])
  // [ 'fuga', 30, 'chocolate' ]
}
```

### `createObject`

|     | A    | B   |
| --- | ---- | --- |
| 1   | hoge | 10  |
| 2   | fuga | 20  |
| 3   | piyo | 20  |

```js
const myFunction = () => {
  const sheet = SpreadsheetApp.getActiveSheet()
  const values = sheet.getDataRange().getValues()
  const object = createObjects(values)

  console.log(object)
  // { hoge: 10, fuga: 20, piyo: 20 }
}
```

### `createArray`

```js
const myFunction = () => {
  const sheet = SpreadsheetApp.getActiveSheet()
  const array = createArray(sheet)

  console.log(array)
  // [{ hoge: 10, fuga: 20, piyo: 20 }, { hoge: 30, fuga: 40, piyo: 40 }]
}
```

### `constructUrl`

```js
const myFunction = () => {
  const baseUrl = 'https://example.com'
  const params = { id: 1, name: 'fuga' }
  const url = constructUrl(baseUrl, params)

  console.log(url)
  // 'https://example.com?id=1&name=fuga'
}
```

### `searchRow`

|     | A    | B   | C         |
| --- | ---- | --- | --------- |
| 1   | name | age | favorite  |
| 2   | hoge | 20  | curry     |
| 3   | fuga | 30  | chocolate |
| 4   | piyo | 40  | coffee    |

```js
const myFunction = () => {
  const sheet = SpreadsheetApp.getActiveSheet()
  const row = searchRow(sheet, 'fuga')

  console.log(row)
  // [3]
}
```

### `URI.js`

URL parser imported from [URI.js](http://medialize.github.io/URI.js/). Please follow the URL below for usage.

- [CODE](https://github.com/kuuhack/google-apps-script-utils/blob/main/src//urlParser.js)
- https://medialize.github.io/URI.js/

### `rpc`

coming soon...
