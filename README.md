# custom_js_select
Custom select v1.0

Create Select:
```js
new SvrSelect(value, values, icon)
```
`value` - {"val": "1", "name": "example1"}
`values` - [{"val": "1", "name": "example1"}, {"val": "2", "name": "example2"}, {"val": "3", "name": "example3"}, {"val": "4", "name": "example4"}, {"val": "5", "name": "example5"}, {"val": "6", "name": "example6"}]
`icon` - SVG(string) || false(Off icon)

Get ready select:
```js
SvrSelect.get_select()
```

Append select into:
```js
SvrSelect.append_in(HTMLElement)
```

Get value select:
```js
SvrSelect.get_value()
```
