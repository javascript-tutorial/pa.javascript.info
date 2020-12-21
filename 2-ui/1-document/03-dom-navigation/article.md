libs:
  - d3
  - domtree

---


# ਡੋਮ ਨੂੰ ਤੁਰਨਾ

DOM ਸਾਨੂੰ ਤੱਤ ਅਤੇ ਉਹਨਾਂ ਦੀ ਸਮੱਗਰੀ ਨਾਲ ਕੁਝ ਵੀ ਕਰਨ ਦੀ ਆਗਿਆ ਦਿੰਦਾ ਹੈ, ਪਰ ਪਹਿਲਾਂ ਸਾਨੂੰ ਸੰਬੰਧਿਤ DOM ਆਬਜੈਕਟ ਤੱਕ ਪਹੁੰਚਣ ਦੀ ਜ਼ਰੂਰਤ ਹੈ.

DOM ਤੇ ਸਾਰੇ ਕਾਰਜ `document` ਇਕਾਈ ਨਾਲ ਸ਼ੁਰੂ ਹੁੰਦੇ ਹਨ. ਇਹ DOM ਦਾ ਮੁੱਖ "ਪ੍ਰਵੇਸ਼ ਬਿੰਦੂ" ਹੈ. ਇਸ ਤੋਂ ਅਸੀਂ ਕਿਸੇ ਵੀ ਨੋਡ ਤੱਕ ਪਹੁੰਚ ਸਕਦੇ ਹਾਂ.

ਲਿੰਕ ਦੀ ਇੱਕ ਤਸਵੀਰ ਇਹ ਹੈ ਜੋ ਡੋਮ ਨੋਡਾਂ ਵਿਚਕਾਰ ਯਾਤਰਾ ਦੀ ਆਗਿਆ ਦਿੰਦੀ ਹੈ:
![](dom-links.svg)

ਆਓ ਉਨ੍ਹਾਂ ਬਾਰੇ ਵਧੇਰੇ ਵਿਸਥਾਰ ਨਾਲ ਵਿਚਾਰ ਕਰੀਏ.

## ਸਿਖਰ 'ਤੇ: documentElement ਅਤੇ body

ਸਿਖਰ ਦੇ tree ਨੋਡ ਸਿੱਧੇ ਤੌਰ 'ਤੇ ਉਪਲਬਧ ਹਨ `document` ਪਰੋਪੇਰਟਿਸ ਦੇ ਰੂਪ ਵਿੱਚ::

`<html>` = `document.documentElement`
: ਸਭ ਤੋਂ ਪੈਹਲਾ ਦਸਤਾਵੇਜ਼ ਨੋਡ ਹੈ `document.documentElement`. ਉਹ `<html>` ਟੈਗ ਦਾ ਡੋਮ ਨੋਡ ਹੈ.

`<body>` = `document.body`
: ਇਕ ਹੋਰ ਵਿਆਪਕ ਤੌਰ ਤੇ ਵਰਤਿਆ ਜਾਂਦਾ ਡੋਮ ਨੋਡ `<body>>` ਐਲੀਮੈਂਟ ਹੈ -- `document.body`.

`<head>` = `document.head`
: `<head>` ਟੈਗ ਇਸ ਤਰਾਂ ਉਪਲੱਬਧ ਹੈ `document.head`.

````warn header="ਇਕ ਕੈਚ ਹੈ: `document.body` ਹੋ ਸਕਦਾ ਹੈ`null`"
ਸਕ੍ਰਿਪਟ ਉਸ ਐਲੀਮੈਂਟ ਤੱਕ ਨਹੀਂ ਪਹੁੰਚ ਸਕਦੀ ਜੋ ਚੱਲਣ ਦੇ ਸਮੇਂ ਮੌਜੂਦ ਨਹੀਂ ਹੈ.

ਖ਼ਾਸਕਰ, ਜੇ ਕੋਈ ਸਕ੍ਰਿਪਟ `<head>` ਦੇ ਅੰਦਰ ਹੈ, then `document.body` ਅਣਉਪਲਬਧ ਹੈ, ਕਿਉਂਕਿ ਬ੍ਰਾਜ਼ਰ ਨੇ ਹਾਲੇ ਇਸਨੂੰ ਨਹੀਂ ਪੜਿਆ.

ਇਸ ਲਈ, ਪਹਿਲੇ ਹੇਠਾਂ ਦਿੱਤੀ ਉਦਾਹਰਣ ਵਿੱਚ `alert` ਦਿਖੇਗਾ `null`:

```html run
<html>

<head>
  <script>
*!*
    alert( "From HEAD: " + document.body ); // null, ਅਜੇ ਕੋਈ <body> ਨਹੀਂ ਹੈ
*/!*
  </script>
</head>

<body>

  <script>
    alert( "From BODY: " + document.body ); // HTMLBodyElement, ਹੁਣ ਇਹ ਮੌਜੂਦ ਹੈ
  </script>

</body>
</html>
```
````

```smart header="ਡੋਮ ਦੁਨੀਆ ਵਿਚ `null` ਦਾ ਮਤਲਬ ਹੈ \"ਮੌਜੂਦ ਨਹੀਂ ਹੈ\""
ਡੋਮ ਵਿਚ, `null` ਦਾ ਅਰਥ ਹੈ "ਮੌਜੂਦ ਨਹੀਂ" ਜਾਂ "ਅਜਿਹਾ ਕੋਈ ਨੋਡ ਨਹੀਂ".
```

## ਬੱਚੇ: ਚਾਈਲਡਨੋਡਜ਼, ਫਸਟ ਚਾਈਲਡ, ਆਖਰੀ ਚਾਈਲਡ

ਇੱਥੇ ਦੋ ਸ਼ਬਦ ਹਨ ਜੋ ਅਸੀਂ ਹੁਣ ਤੋਂ ਇਸਤੇਮਾਲ ਕਰਾਂਗੇ:

- **ਚਾਈਲਡ ਨੋਡ (ਜਾਂ ਬੱਚੇ) ** - ਉਹ ਐਲਿਮੈਂਟ ਜੋ ਸਿੱਧੇ ਬੱਚੇ ਹੁੰਦੇ ਹਨ. ਦੂਜੇ ਸ਼ਬਦਾਂ ਵਿਚ, ਉਹ ਇਕ ਦਿੱਤੇ ਅੰਦਰ ਬਿਲਕੁਲ ਬਸੇ ਹੋਏ ਹਨ. ਉਦਾਹਰਣ ਦੇ ਲਈ, `<head>` ਅਤੇ `<body>` ਬੱਚੇ ਹਨ `<html>` ਐਲਿਮੈਂਟ ਦੇ .
- **ਔਲਾਦ** -- ਉਹ ਸਾਰੇ ਏਲੇਲਮੈਂਟ ਜੋ ਦਿੱਤੇ ਗਏ ਹਨ ਇੱਕ ਦੂਜੇ ਵਿੱਚ ਬੱਝੇ ਹੋਏ ਹਨ, ਸਮੇਤ ਬੱਚੇ, ਉਨ੍ਹਾਂ ਦੇ ਬੱਚੇ ਅਤੇ ਹੋਰ

ਉਦਾਹਰਣ ਲਈ, ਇਥੇ `<body>` ਬੱਚੇ ਹਨ `<div>` ਅਤੇ `<ul>` (ਅਤੇ ਕੁਝ ਖਾਲੀ ਟੈਕਸਟ ਨੋਡ):

```html run
<html>
<body>
  <div>Begin</div>

  <ul>
    <li>
      <b>Information</b>
    </li>
  </ul>
</body>
</html>
```

...ਅਤੇ `<body>` ਦੇ ਵੰਸ਼ਜ `<div>`, `<ul>` ਹੀ ਸਿਰਫ ਸਿੱਧੇ ਬੱਚੇ ਨਹੀਂ ਹਨ  ਪਰ ਹੋਰ ਵੀ ਡੂੰਘੇ ਬਝੈ ਐਲਿਮੈਂਟ, ਜਿਵੇ ਕੀ `<li>` (ਦਾ ਇੱਕ ਬੱਚਾ`<ul>`) ਅਤੇ `<b>` (ਦਾ ਇੱਕ ਬੱਚਾ `<li>`) -- ਸਾਰੀ ਸਬਟ੍ਰੀ.

**`ਚਾਈਲਡ ਨੋਡਸ` ਸੰਗ੍ਰਹਿ ਟੈਕਸਟ ਨੋਡਾਂ ਸਮੇਤ, ਸਾਰੇ ਚਿਲਡ ਨੋਡਾਂ ਦੀ ਸੂਚੀ ਹੈ.**

ਹੇਠਾਂ ਦਿੱਤੀ ਉਦਾਹਰਣ `document.body` ਦੇ ਬੱਚਿਆਂ ਨੂੰ ਦਰਸਾਉਂਦੀ ਹੈ :

```html run
<html>
<body>
  <div>Begin</div>

  <ul>
    <li>Information</li>
  </ul>

  <div>End</div>

  <script>
*!*
    for (let i = 0; i < document.body.childNodes.length; i++) {
      alert( document.body.childNodes[i] ); // Text, DIV, Text, UL, ..., SCRIPT
    }
*/!*
  </script>
  ... ਹੋਰ ਚੀਜ਼ਾਂ ...
</body>
</html>
```

ਕਿਰਪਾ ਕਰਕੇ ਇੱਥੇ ਇੱਕ ਦਿਲਚਸਪ ਵੇਰਵਾ ਨੋਟ ਕਰੋ. ਅਗਰ ਅਸੀਂ ਉਪਰੋਕਤ ਉਦਾਹਰਣ ਚਲਾਉਂਦੇ ਹਾਂ, ਦਿਖਾਇਆ ਗਿਆ ਆਖਰੀ ਤੱਤ `<script> ਹੈ. ਦਰਅਸਲ, ਦਸਤਾਵੇਜ਼ ਵਿੱਚ ਹੇਠਾਂ ਵਧੇਰੇ ਚੀਜ਼ਾਂ ਹਨ, ਪਰ ਸਕ੍ਰਿਪਟ ਲਾਗੂ ਹੋਣ ਦੇ ਸਮੇਂ ਬ੍ਰਾਜ਼ਰ ਨੇ ਅਜੇ ਇਸਨੂੰ ਨਹੀਂ ਪੜਿਆ, ਇਸਲਈ ਸਕ੍ਰਿਪਟ ਇਸਨੂੰ ਨਹੀਂ ਵੇਖਦੀ

**Properties `firstChild` ਅਤੇ `lastChild` ਪਹਿਲੇ ਅਤੇ ਆਖਰੀ ਬੱਚਿਆਂ ਨੂੰ ਤੇਜ਼ ਪਹੁੰਚ ਦੇਂਦੀ ਹੀ.**

ਏਹ ਸਿਰਫ ਸ਼ੋਰਟਹੈਂਡ ਹਨ. ਜੇ ਇੱਥੇ ਬੱਚੇ ਦੇ ਨੋਡ ਮੌਜੂਦ ਹਨ, ਤਾਂ ਹੇਠਾਂ ਦਿੱਤਾ ਹਮੇਸ਼ਾਂ ਸਹੀ ਹੁੰਦਾ ਹੈ:
```js
elem.childNodes[0] === elem.firstChild
elem.childNodes[elem.childNodes.length - 1] === elem.lastChild
```

ਇਕ ਵਿਸ਼ੇਸ਼ ਫੰਕਸ਼ਨ ਵੀ ਹੈ `elem.hasChildNodes()` ਇਹ ਵੇਖਣ ਲਈ ਕਿ ਇੱਥੇ ਕੋਈ ਚਿਲਡ ਨੋਡਸ ਹਨ ਜਾਂ ਨਹੀਂ.

### ਡੋਮ ਸੰਗ੍ਰਹਿ

ਜਿਵੇਂ ਕਿ ਅਸੀਂ ਵੇਖ ਸਕਦੇ ਹਾਂ, `childNodes` ਇੱਕ ਐਰੇ ਵਰਗਾ ਦਿਖਾਈ ਦਿੰਦਾ ਹੈ. ਪਰ ਅਸਲ ਵਿੱਚ ਇਹ ਇੱਕ ਐਰੇ ਨਹੀਂ, ਬਲਕਿ ਇੱਕ * ਸੰਗ੍ਰਹਿ * - ਇੱਕ ਵਿਸ਼ੇਸ਼ ਐਰੇ-ਵਰਗੇ ਆਵਰਤੀ ਆਬਜੈਕਟ ਹੈ.

ਇਸ ਦੇ ਦੋ ਮਹੱਤਵਪੂਰਨ ਨਤੀਜੇ ਹਨ:

1. ਅਸੀਂ ਇਸ ਨੂੰ ਦੁਹਰਾਉਣ ਲਈ `for..of` ਦੀ ਵਰਤੋਂ ਕਰ ਸਕਦੇ ਹਾਂ:
  ```js
  for (let node of document.body.childNodes) {
    alert(node); // ਸੰਗ੍ਰਹਿ ਦੇ ਸਾਰੇ ਨੋਡਾਂ ਨੂੰ ਦਰਸਾਉਂਦਾ ਹੈ
  }
  ```
  ਅਜਿਹਾ ਇਸ ਲਈ ਕਿਉਂਕਿ ਇਹ ਦੁਹਰਾਉਣ ਯੋਗ ਹੈ (ਜ਼ਰੂਰਤ ਅਨੁਸਾਰ. Symbol.iterator` properties ਪ੍ਰਦਾਨ ਕਰਦਾ ਹੈ).

2. ਐਰੇ methods ਕੰਮ ਨਹੀਂ ਕਰਨਗੇ, ਕਿਉਂਕਿ ਇਹ ਐਰੇ ਨਹੀਂ ਹੈ:
  ```js run
  alert(document.body.childNodes.filter); // undefined (there's no filter method!)
  ```

ਪਹਿਲੀ ਚੀਜ਼ ਚੰਗੀ ਹੈ. ਦੂਜਾ ਸਹਿਣਸ਼ੀਲ ਹੈ, ਕਿਉਂਕਿ ਅਸੀਂ `Array.from`ਦੀ ਵਰਤੋਂ ਕਰ ਸਕਦੇ ਹਾਂ  ਸੰਗ੍ਰਹਿ ਵਿਚੋਂ ਇਕ "ਅਸਲ" ਐਰੇ ਬਣਾਉਣ ਲਈ, ਜੇ ਅਸੀਂ ਐਰੇ methods ਨੂੰ ਚਾਹੁੰਦੇ ਹਾਂ:

  ```js run
  alert( Array.from(document.body.childNodes).filter ); // function
  ```

```warn header="DOM ਸੰਗ੍ਰਹਿ ਸਿਰਫ-ਪੜ੍ਹਨ ਲਈ ਹਨ"
ਡੋਮ ਸੰਗ੍ਰਹਿ ਅਤੇ ਹੋਰ ਵੀ ਬਹੁਤ ਕੁਝ -- *ਸਾਰੇ * ਨੇਵੀਗੇਸ਼ਨ properties ਜੋ ਇਸ ਅਧਿਆਇ ਵਿਚ ਸੂਚੀਬੱਧ ਹਨ ਰੀਡ-ਔਨਲੀ ਹਨ.

ਅਸੀਂ ਕਿਸੇ ਬੱਚੇ ਨੂੰ ਨਿਰਧਾਰਤ ਕਰਕੇ ਕਿਸੇ ਹੋਰ ਚੀਜ਼ ਨਾਲ ਨਹੀਂ ਬਦਲ ਸਕਦੇ ਜਿਵੇਂ ਕੀ `childNodes[i] = ...`.

DOM ਬਦਲਣ ਲਈ ਹੋਰ ਤਰੀਕਿਆਂ ਦੀ ਜਰੂਰਤ ਹੈ. ਅਸੀਂ ਉਨ੍ਹਾਂ ਨੂੰ ਅਗਲੇ ਅਧਿਆਇ ਵਿਚ ਦੇਖਾਂਗੇ.
```

```warn header="ਡੋਮ ਸੰਗ੍ਰਹਿ ਲਾਈਵ ਹਨ"
ਮਾਮੂਲੀ ਅਪਵਾਦਾਂ ਦੇ ਨਾਲ ਲਗਭਗ ਸਾਰੇ DOM ਸੰਗ੍ਰਹਿ * ਲਾਈਵ * ਹਨ. ਦੂਜੇ ਸ਼ਬਦਾਂ ਵਿਚ, ਉਹ DOM ਦੀ ਮੌਜੂਦਾ ਸਥਿਤੀ ਨੂੰ ਦਰਸਾਉਂਦੇ ਹਨ.

ਜੇ ਅਸੀਂ ਇਕ ਹਵਾਲਾ ਰੱਖਦੇ ਹਾਂ`elem.childNodes` ਵਲ, ਅਤੇ DOM ਵਿੱਚ ਨੋਡ ਸ਼ਾਮਲ / ਹਟਾਓ, ਤਦ ਉਹ ਆਪਣੇ ਆਪ ਹੀ ਸੰਗ੍ਰਹਿ ਵਿੱਚ ਪ੍ਰਗਟ ਹੋਣਗੇ.
```

````warn header="ਸੰਗ੍ਰਹਿ ਨੂੰ ਲੂਪ ਕਰਨ ਲਈ `for..in` ਦੀ ਵਰਤੋਂ ਨਾ ਕਰੋ"
ਸੰਗ੍ਰਹਿ `for..of` ਦੀ ਵਰਤੋਂ ਨਾਲ ਦੁਹਰਾ ਸਕਦੇ ਹਨ. ਕਈ ਵਾਰ ਲੋਕ ਉਸ ਲਈ `for..in` ਦੀ ਵਰਤੋਂ ਕਰਨ ਦੀ ਕੋਸ਼ਿਸ਼ ਕਰਦੇ ਹਨ.
ਕਿਰਪਾ ਕਰਕੇ ਨਾ ਕਰੋ. `For..in` ਲੂਪ ਸਾਰੀਆਂ ਅਣਗਿਣਤ ਵਿਸ਼ੇਸ਼ਤਾਵਾਂ ਤੇ ਦੁਹਰਾਉਂਦਾ ਹੈ. ਅਤੇ ਸੰਗ੍ਰਹਿ ਦੀਆਂ ਕੁਝ "ਵਾਧੂ" ਬਹੁਤ ਘੱਟ ਵਰਤੋਂ ਵਾਲੀਆਂ ਵਿਸ਼ੇਸ਼ਤਾਵਾਂ ਹਨ ਜੋ ਅਸੀਂ ਆਮ ਤੌਰ 'ਤੇ ਪ੍ਰਾਪਤ ਨਹੀਂ ਕਰ ਸਕਦੇ:
```html run
<body>
<script>
  // shows 0, 1, length, item, values and more.
  for (let prop in document.body.childNodes) alert(prop);
</script>
</body>
````

## ਭੈਣ-ਭਰਾ ਅਤੇ ਮਾਪੇ

* ਭੈਣ-ਭਰਾ * ਇਕੋ ਇਕ ਮਾਪੇ ਦੇ ਬੱਚੇ ਹਨ.

ਉਦਾਹਰਣ ਦੇ ਲਈ, ਇੱਥੇ `<head>` ਅਤੇ `<body>` ਭੈਣ-ਭਰਾ ਹਨ:

```html
<html>
  <head>...</head><body>...</body>
</html>
```

- `<body>` ਨੂੰ "ਅਗਲਾ" ਜਾਂ "ਸੱਜਾ" ਭੈਣ-ਭਰਾ ਕਿਹਾ ਜਾਂਦਾ ਹੈ `<head>` ਦਾ,
- `<head>` ਨੂੰ "ਪਿਛਲੇ" ਜਾਂ "ਖੱਬਾ" ਭੈਣ-ਭਰਾ ਕਿਹਾ ਜਾਂਦਾ ਹੈ `<body>` ਦਾ.

ਅਗਲਾ ਭੈਣ-ਭਰਾ ਹੈ `nextSibling` property, ਅਤੇ ਇੱਕ ਪਿਛਲਾ- `previousSibling`.

ਮਾਪੇ ਦੇ ਤੌਰ ਤੇ ਉਪਲੱਬਧ ਹੈ `parentNode`.

For example:

<<<<<<< HEAD
```js
// <body> ਦੇ ਮਾਪੇ <html> ਹੈ
=======
```js run
// parent of <body> is <html>
>>>>>>> fc3f811c03ca97ff8304271bb2b918413bed720f
alert( document.body.parentNode === document.documentElement ); // true

// <head> ਦੇ ਬਾਅਦ <body> ਹੈ
alert( document.head.nextSibling ); // HTMLBodyElement

// <body> ਜਾਣ ਤੋਂ ਪਹਿਲਾਂ <head>
alert( document.body.previousSibling ); // HTMLHeadElement
```

## ਐਲੀਮੈਂਟ-ਸਿਰਫ ਨੈਵੀਗੇਸ਼ਨ

ਉੱਪਰ ਸੂਚੀਬੱਧ ਨੇਵੀਗੇਸ਼ਨ ਵਿਸ਼ੇਸ਼ਤਾਵਾਂ * ਸਾਰੇ * ਨੋਡਾਂ ਦਾ ਹਵਾਲਾ ਦਿੰਦੀਆਂ ਹਨ. ਉਦਾਹਰਣ ਲਈ, `childNodes` ਅਸੀਂ ਦੋਵੇਂ ਟੈਕਸਟ ਨੋਡਸ, ਐਲੀਮੈਂਟ ਨੋਡਸ, ਅਤੇ ਟਿੱਪਣੀ ਨੋਡਸ ਨੂੰ ਦੇਖ ਸਕਦੇ ਹਾਂ ਜੇ ਇੱਥੇ ਮੌਜੂਦ ਹੈ.

ਪਰ ਬਹੁਤ ਸਾਰੇ ਕੰਮਾਂ ਲਈ ਅਸੀਂ ਟੈਕਸਟ ਜਾਂ ਟਿੱਪਣੀ ਨੋਡ ਨਹੀਂ ਚਾਹੁੰਦੇ.ਅਸੀਂ ਐਲੀਮੈਂਟ ਨੋਡਾਂ ਵਿੱਚ ਹੇਰਾਫੇਰੀ ਕਰਨਾ ਚਾਹੁੰਦੇ ਹਾਂ ਜੋ ਟੈਗਾਂ ਨੂੰ ਦਰਸਾਉਂਦੇ ਹਨ ਅਤੇ ਪੰਨੇ ਦੇ ਢਾਂਚੇ ਨੂੰ ਬਣਾਉਂਦੇ ਹਨ.

ਤਾਂ ਆਓ ਹੋਰ ਨੇਵੀਗੇਸ਼ਨ ਲਿੰਕ ਵੇਖੀਏ ਜੋ ਸਿਰਫ * ਐਲੀਮੈਂਟ ਨੋਡ * ਨੂੰ ਧਿਆਨ ਵਿੱਚ ਰੱਖਦੇ ਹਨ:

![](dom-links-elements.svg)

ਲਿੰਕ ਉੱਪਰ ਦਿੱਤੇ ਸ਼ਬਦਾਂ ਦੇ ਸਮਾਨ ਹਨ, ਸਿਰਫ ਅੰਦਰ `ਐਲੀਮੈਂਟ` ਸ਼ਬਦ ਦੇ ਨਾਲ:

- `children` -- ਸਿਰਫ ਉਹ ਬੱਚੇ ਜੋ ਐਲਿਮੈਂਟ ਨੋਡ ਹਨ.
- `firstElementChild`, `lastElementChild` -- ਪਹਿਲੇ ਅਤੇ ਆਖਰੀ ਐਲਿਮੈਂਟ ਦੇ ਬੱਚੇ.
- `previousElementSibling`, `nextElementSibling` -- ਗੁਆਂਢੀਂ ਐਲਿਮੈਂਟ.
- `parentElement` -- ਮੁੱਢਲਾ ਐਲਿਮੈਂਟ.

````smart header="ਕਿਉਂ `parentElement`? ਕੀ ਪੇਰੇਂਟ ਇਕ ਐਲਿਮੈਂਟ * ਨਹੀਂ * ਹੋ ਸਕਦੇ ਹਨ?"
`parentElement` ਪ੍ਰੋਪਰਟੀ "ਐਲਿਮੈਂਟ" ਪੇਰੇਂਟ ਨੂੰ ਵਾਪਸ ਕਰਦੀ ਹੈ, ਜਦਕਿ `parentNode` "ਕੋਈ ਨੋਡ" ਕੋਈ ਵੀ ਮਾਪਾ ਵਾਪਸ ਕਰਦੀ ਹੈ. ਇਹ properties ਆਮ ਤੌਰ 'ਤੇ ਇਕੋ ਹੁੰਦੀਆਂ ਹਨ: ਉਹ ਦੋਵੇਂ ਤੋਂ ਪ੍ਰਾਪਤ ਹੁੰਦਾ ਹੈ parent.

`document.documentElement` ਇਕ ਅਪਵਾਦ ਹੈ:

```js run
alert( document.documentElement.parentNode ); // document
alert( document.documentElement.parentElement ); // null
```

ਕਾਰਨ ਇਹ ਹੈ ਕਿ ਰੂਟ ਨੋਡ `document.documentElement` (`<html>`) ਹੈ `document` ਇਸ ਦੇ ਮਾਪੇ ਹਨ. ਪਰ `document` ਇਕ ਐਲੀਮੈਂਟ ਨੋਡ ਨਹੀਂ ਹੈ, ਇਸ ਲਈ `parentNode` ਇਸ ਨੂੰ ਵਾਪਸ ਕਰਦਾ ਹੈ ਅਤੇ `parentElement` ਨਹੀ ਕਰਦਾ.

ਇਹ ਵਿਸਥਾਰ ਲਾਭਦਾਇਕ ਹੋ ਸਕਦਾ ਹੈ ਜਦੋਂ ਅਸੀਂ ਇੱਕ ਲੋੜੀਂਦੇ `elem` ਤੋਂ  `<html>` ਤੱਕ ਜਾਣਾ ਚਾਹੁੰਦੇ ਹਾਂ, ਪਰ `document` ਤੱਕ ਨਹੀਂ:
```js
while(elem = elem.parentElement) { // <html> ਤਕ ਚਲੇ ਜਾਓ 
  alert( elem );
}
```
````

ਚਲੋ ਉਪਰੋਕਤ ਉਦਾਹਰਣਾਂ ਵਿੱਚੋਂ ਇੱਕ ਨੂੰ ਸੋਧੋ: ਬਦਲੋ `childNodes` ਦੇ ਨਾਲ `children`. ਹੁਣ ਇਹ ਸਿਰਫ ਐਲਿਮੈਂਟਸ ਦਿਖਾਉਂਦਾ ਹੈ:

```html run
<html>
<body>
  <div>Begin</div>

  <ul>
    <li>Information</li>
  </ul>

  <div>End</div>

  <script>
*!*
    for (let elem of document.body.children) {
      alert(elem); // DIV, UL, DIV, SCRIPT
    }
*/!*
  </script>
  ...
</body>
</html>
```

## ਹੋਰ ਲਿੰਕ: ਟੇਬਲ [#dom-navigation-tables]

ਹੁਣ ਤੱਕ ਅਸੀਂ ਮੁਢਲੀ ਨੇਵੀਗੇਸ਼ਨ ਵਿਸ਼ੇਸ਼ਤਾਵਾਂ ਦਾ ਵੇਰਵਾ ਦਿੱਤਾ ਹੈ.

ਕੁਝ ਕਿਸਮ ਦੇ DOM ਐਲਿਮੈਂਟਸ ਵਾਧੂ ਵਿਸ਼ੇਸ਼ਤਾਵਾਂ ਪ੍ਰਦਾਨ ਕਰ ਸਕਦੇ ਹਨ, ਉਨ੍ਹਾਂ ਦੀ ਕਿਸਮ ਲਈ ਖਾਸ, ਸਹੂਲਤ ਲਈ.

ਟੇਬਲ ਇਸ ਦੀ ਇੱਕ ਵਧੀਆ ਉਦਾਹਰਣ ਹਨ, ਅਤੇ ਇੱਕ ਵਿਸ਼ੇਸ਼ ਮਹੱਤਵਪੂਰਣ ਕੇਸ ਨੂੰ ਦਰਸਾਉਂਦੇ ਹਨ:

**`<table>`** ਐਲਿਮੈਂਟ ਦੀ ਸਹਿਯੋਗੀ properties ਹੈ (ਉੱਪਰ ਦਿੱਤੇ ਤੋਂ ਇਲਾਵਾ) :
- `table.rows` -- ਟੇਬਲ ਦੇ `<tr>` ਤੱਤਾਂ ਦਾ ਕਲਕਸ਼ਨ.
- `table.caption/tHead/tFoot` -- ਐਲੀਮੈਂਟਸ <caption> `,` <thead> `,` <tfoot> `ਦਾ ਹਵਾਲਾ.
- `table.tBodies` -- `<tbody>` ਐਲਿਮੈਂਟਸ ਦੀ ਕੱਲੈਕਸ਼ਨ (ਮਿਆਰ ਦੇ ਅਨੁਸਾਰ ਬਹੁਤ ਸਾਰੇ ਹੋ ਸਕਦੇ ਹਨ, ਪਰ ਇੱਥੇ ਹਮੇਸ਼ਾਂ ਘੱਟੋ ਘੱਟ ਇੱਕ ਹੋਵੇਗਾ - ਭਾਵੇਂ ਇਹ ਸਰੋਤ HTML ਵਿੱਚ ਨਹੀਂ ਹੈ, ਬ੍ਰਾਜ਼ਰ ਇਸਨੂੰ DOM ਵਿੱਚ ਪਾ ਦੇਵੇਗਾ).

**`<thead>`, `<tfoot>`, `<tbody>`** ਐਲਿਮੈਂਟ `row` ਦੀ ਪ੍ਰੋਪਰਟੀ ਪ੍ਰਦਾਨ ਕਰਦੇ ਹਨ:
- `tbody.rows` -- ਅੰਦਰ `<tr>. ਦਾ ਸੰਗ੍ਰਹਿ.

**`<tr>`:**
- `tr.cells` -- ਦਿੱਤੇ `<tr>` ਦੇ ਅੰਦਰ `<td>` ਅਤੇ `<th>` ਸੈੱਲਾਂ ਦਾ ਸੰਗ੍ਰਹਿ.
- `tr.sectionRowIndex` -- ਦਿੱਤੀ ਗਈ ਸਥਿਤੀ (ਇੰਡੈਕਸ) `<tr>` inside the enclosing `<thead>/<tbody>/<tfoot>`.
- `tr.rowIndex` -- ਸਮੁੱਚੇ ਤੌਰ ਤੇ ਵਿੱਚ all <tr> ਦੀ ਗਿਣਤੀ (ਸਾਰੀਆਂ ਸਾਰਣੀ ਦੀਆਂ ਕਤਾਰਾਂ ਸਮੇਤ).

**`<td>` and `<th>`:**
- `td.cellIndex` -- ਬੰਦ `<tr>` ਦੇ ਅੰਦਰ ਸੈੱਲ ਦੀ ਸੰਖਿਆ.

ਵਰਤੋਂ ਦੀ ਇੱਕ ਉਦਾਹਰਣ:

```html run height=100
<table id="table">
  <tr>
    <td>one</td><td>two</td>
  </tr>
  <tr>
    <td>three</td><td>four</td>
  </tr>
</table>

<script>
  // get td with "two" (first row, second column)
  let td = table.*!*rows[0].cells[1]*/!*;
  td.style.backgroundColor = "red"; // highlight it
</script>
```

ਨਿਰਧਾਰਨ: [tabular data](https://html.spec.whatwg.org/multipage/tables.html).

HTML ਫਾਰਮ ਲਈ ਅਤਿਰਿਕਤ ਨੇਵੀਗੇਸ਼ਨ ਵਿਸ਼ੇਸ਼ਤਾਵਾਂ ਹਨ. ਜਦੋਂ ਅਸੀਂ ਫਾਰਮਾਂ ਨਾਲ ਕੰਮ ਕਰਨਾ ਅਰੰਭ ਕਰਾਂਗੇ ਅਸੀਂ ਉਨ੍ਹਾਂ ਨੂੰ ਬਾਅਦ ਵਿੱਚ ਵੇਖਾਂਗੇ.

## ਸਾਰ

ਇੱਕ ਡੋਮ ਨੋਡ ਦਿੱਤੇ ਜਾਣ ਤੇ, ਅਸੀਂ ਨੇਵੀਗੇਸ਼ਨ ਵਿਸ਼ੇਸ਼ਤਾਵਾਂ ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਇਸਦੇ ਨਜ਼ਦੀਕੀ ਗੁਆਂਡੀਆਂ ਕੋਲ ਜਾ ਸਕਦੇ ਹਾਂ.

ਉਨ੍ਹਾਂ ਦੇ ਦੋ ਮੁੱਖ ਸਮੂਹ ਹਨ

- ਸਾਰੇ ਨੋਡਾਂ ਲਈ: `parentNode`, `childNodes`, `firstChild`, `lastChild`, `previousSibling`, `nextSibling`.
- ਸਿਰਫ ਐਲੀਮੈਂਟ ਨੋਡਜ਼ ਲਈ: `parentElement`, `children`, `firstElementChild`, `lastElementChild`, `previousElementSibling`, `nextElementSibling`.

ਕੁਝ ਕਿਸਮ ਦੇ DOM ਐਲਿਮੈਂਟਸ ਉਧਾਰਣ, ਟੇਬਲ, ਉਨ੍ਹਾਂ ਦੀ ਸਮਗਰੀ ਨੂੰ ਐਕਸੈਸ ਕਰਨ ਲਈ ਵਾਧੂ ਵਿਸ਼ੇਸ਼ਤਾਵਾਂ ਅਤੇ ਸੰਗ੍ਰਹਿ ਪ੍ਰਦਾਨ ਕਰਦੇ ਹਨ.
