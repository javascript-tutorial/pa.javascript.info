ਇੱਥੇ ਬਹੁਤ ਸਾਰੇ ਤਰੀਕੇ ਹਨ, ਉਦਾਹਰਣ ਵਜੋਂ:

`<div>` DOM ਨੋਡ:

```js
document.body.firstElementChild
// ਜਾਂ
document.body.children[0]
// ਜਾਂ (ਪਹਿਲਾ ਨੋਡ ਸਪੇਸ ਹੈ, ਇਸਲਈ ਅਸੀਂ ਦੂਜਾ ਸਥਾਨ ਲੈਂਦੇ ਹਾਂ)
document.body.childNodes[1]
```

`<ul>`DOM ਨੋਡ:

```js
document.body.lastElementChild
// or
document.body.children[1]
```

ਦੂਜਾ`<li>` (ਪੀਟ ਨਾਲ):

```js
// ਪ੍ਰਾਪਤ ਕਰੋ <ul>,ਅਤੇ ਫਿਰ ਇਸ ਦਾ ਆਖਰੀ ਏਲੇਮੈਂਟ ਵਾਲਾ ਬੱਚਾ ਪ੍ਰਾਪਤ ਕਰੋ
document.body.lastElementChild.lastElementChild
```
