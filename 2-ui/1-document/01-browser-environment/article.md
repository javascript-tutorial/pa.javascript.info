# ਬਰਾਜ਼ਰ ਵਾਤਾਵਰਣ, ਸਪੇਸੀਫੀਕੇਸਨ

ਜਾਵਾ ਸਕ੍ਰਿਪਟ ਭਾਸ਼ਾ ਸ਼ੁਰੂ ਵਿੱਚ ਵੈਬ ਬ੍ਰਾਜ਼ਰਾਂ ਲਈ ਬਣਾਈ ਗਈ ਸੀ. ਉਦੋਂ ਤੋਂ ਇਹ ਵਿਕਸਤ ਹੋਈ ਹੈ ਅਤੇ ਬਹੁਤ ਸਾਰੀਆਂ ਵਰਤੋਂ ਅਤੇ ਪਲੇਟਫਾਰਮਾਂ ਵਾਲੀ ਇੱਕ ਭਾਸ਼ਾ ਬਣ ਗਈ ਹੈ।

<<<<<<< HEAD
ਇਸ਼ਦਾ ਪਲੇਟਫਾਰਮ ਇੱਕ ਬ੍ਰਾਉਜ਼ਰ, ਜਾਂ ਇੱਕ ਵੈੱਬ-ਸਰਵਰ ਜਾਂ ਕੋਈ ਹੋਰ * ਹੋਸਟ * ਹੋ ਸਕਦਾ ਹੈ, ਇੱਕ ਕਾਫੀ ਮਸ਼ੀਨ ਵੀ ਹੋ ਸਕਦੀ ਹੈ. ਉਨ੍ਹਾਂ ਵਿਚੋਂ ਹਰੇਕ ਪਲੇਟਫਾਰਮ-ਵਿਸ਼ੇਸ਼ ਲਈ ਕਾਰਜਕੁਸ਼ਲਤਾ ਪ੍ਰਦਾਨ ਕਰਦਾ ਹੈ. ਜਾਵਾ ਸਕ੍ਰਿਪਟ ਨਿਰਧਾਰਨ ਇੱਕ * ਹੋਸਟ ਵਾਤਾਵਰਣ * ਨੂੰ ਲੋਚਦਾ ਹੈ.
=======
A platform may be a browser, or a web-server or another *host*, even a "smart" coffee machine, if it can run JavaScript. Each of them provides platform-specific functionality. The JavaScript specification calls that a *host environment*.
>>>>>>> 193319c963b9ba86ac7d9590f7261a36ecdcc4d2

ਇੱਕ ਮੇਜ਼ਬਾਨ ਵਾਤਾਵਰਣ ਆਪਣੀ ਖੁਦ ਦੀਆਂ ਵਸਤੂਆਂ ਪ੍ਰਦਾਨ ਕਰਦਾ ਹੈ ਅਤੇ ਮੇਨ ਭਾਸ਼ਾ ਲਈ ਵਾਧੂ ਕਾਰਜ ਕਰਦਾ ਹੈ. ਵੈੱਬ ਬਰਾਜ਼ਰ ਵੈਬ ਪੇਜਾਂ ਨੂੰ ਨਿਯੰਤਰਿਤ ਕਰਨ ਦਾ ਜ਼ਰੀਆ ਦਿੰਦੇ ਹਨ. Node।js ਸਰਵਰ-ਸਾਈਡ ਵਿਸ਼ੇਸ਼ਤਾਵਾਂ, ਅਤੇ ਹੋਰ ਖ਼ਾਸ ਵਿਸ਼ੇਸਤਾਵਾਂ ਪ੍ਰਦਾਨ ਕਰਦਾ ਹੈ.

<<<<<<< HEAD
ਜਦੋਂ ਜਾਵਾ ਸਕ੍ਰਿਪਟ ਇੱਕ ਵੈੱਬ-ਬ੍ਰਾਜ਼ਰ ਵਿੱਚ ਚਲਦੀ ਹੈ ਤਾਂ ਇੱਥੇ ਸਾਡੇ ਕੋਲ ਇੱਕ ਪੰਛੀ ਦਾ ਨਜ਼ਰੀਆ ਦਰਸਾਉਂਦਾ ਹੈ:
=======
Here's a bird's-eye view of what we have when JavaScript runs in a web browser:
>>>>>>> 193319c963b9ba86ac7d9590f7261a36ecdcc4d2

![](windowObjects.svg)

ਇੱਥੇ ਇੱਕ "ਰੂਟ" ਆਬਜੈਕਟ ਹੈ ਜਿਸ ਨੂੰ `ਵਿੰਡੋ` ਕਹਿੰਦੇ ਹਨ. ਇਸ ਦੀਆਂ ਦੋ ਭੂਮਿਕਾਵਾਂ ਹਨ:

1. ਪਹਿਲਾਂ, ਜਾਵਾ ਸਕ੍ਰਿਪਟ ਕੋਡ ਲਈ ਇਹ ਇਕ ਗਲੋਬਲ ਆਬਜੈਕਟ ਹੈ, ਜਿਵੇਂ ਕਿ ਇਸ ਚੈਪਟਰ ਵਿਚ ਦੱਸਿਆ ਗਿਆ ਹੈ <info:global-object>.
2. ਦੂਜਾ, ਇਹ "ਬ੍ਰਾਜ਼ਰ ਵਿੰਡੋ" ਨੂੰ ਦਰਸਾਉਂਦਾ ਹੈ ਅਤੇ ਇਸਨੂੰ ਨਿਯੰਤਰਣ ਕਰਨ ਲਈ methods ਪ੍ਰਦਾਨ ਕਰਦਾ ਹੈ.

ਉਦਾਹਰਣ ਦੇ ਲਈ, ਇੱਥੇ ਅਸੀਂ ਇਸਨੂੰ ਇੱਕ ਗਲੋਬਲ ਆਬਜੈਕਟ ਦੇ ਤੌਰ ਤੇ ਵਰਤਦੇ ਹਾਂ:

```js run
function sayHi() {
  alert("Hello");
}

// ਗਲੋਬਲ ਫੰਕਸ਼ਨ ਗਲੋਬਲ ਆਬਜੈਕਟ ਦੇ methods ਹਨ:
window.sayHi();
```

ਅਤੇ ਇੱਥੇ ਅਸੀਂ ਇਸਨੂੰ ਇੱਕ ਵਿੰਡੋ ਦੇ ਤੌਰ ਤੇ ਵਰਤਦੇ ਹਾਂ, ਵਿੰਡੋ ਦੀ ਉਚਾਈ ਵੇਖਣ ਲਈ:

```js run
alert(window.innerHeight); // ਅੰਦਰੂਨੀ ਵਿੰਡੋ ਦੀ ਉਚਾਈ
```

ਇੱਥੇ ਹੋਰ ਵਿੰਡੋ-ਵਿਸ਼ੇਸ਼ methods ਅਤੇ properties ਹਨ, ਅਸੀਂ ਉਨ੍ਹਾਂ ਨੂੰ ਬਾਅਦ ਵਿੱਚ ਕਵਰ ਕਰਾਂਗੇ.
## DOM (Document Object Model)

Document Object Model, ਜਾਂ DOM ਸੰਖੇਪ ਲਈ, ਸਾਰੇ ਪੰਨੇ ਦੀ ਸਮਗਰੀ ਨੂੰ ਇਕਾਈ ਦੇ ਤੌਰ ਤੇ ਦਰਸਾਉਂਦਾ ਹੈ ਜਿਸ ਨੂੰ ਸੋਧਿਆ ਜਾ ਸਕਦਾ ਹੈ.

 `document` ਪੇਜ 'ਤੇ ਇਕਾਈ ਦਾ ਮੁੱਖ "ਦਾਖਲਾ ਬਿੰਦੂ" ਹੈ. ਅਸੀਂ ਇਸ ਦੀ ਵਰਤੋਂ ਕਰਦੇ ਹੋਏ ਪੇਜ 'ਤੇ ਕੁਝ ਵੀ ਬਦਲ ਸਕਦੇ ਹਾਂ ਜਾਂ ਬਣਾ ਸਕਦੇ ਹਾਂ.

ਉਦਾਹਰਣ ਦੇ ਲਈ:
```js run
// ਬੈਕਗ੍ਰਾਉਂਡ ਦੇ ਰੰਗ ਨੂੰ ਲਾਲ ਵਿੱਚ ਬਦਲੋ
document.body.style.background = "red";

// ਇਸਨੂੰ 1 ਸਕਿੰਟ ਬਾਅਦ ਵਾਪਸ ਬਦਲੋ
setTimeout(() => document.body.style.background = "", 1000);
```

<<<<<<< HEAD
ਇੱਥੇ ਅੱਸੀ ਵਰਤਿਆ`document.body.style`, ਪਰ ਉਥੇ ਬਹੁਤ ਕੁਝ ਹੈ, ਹੋਰ ਵੀ ਬਹੁਤ ਕੁਝ. Properties ਅਤੇ methods ਨਿਰਧਾਰਨ ਵਿੱਚ ਦੱਸਿਆ ਗਿਆ ਹੈ:

- **DOM Living Standard** at <https://dom.spec.whatwg.org>
=======
Here we used `document.body.style`, but there's much, much more. Properties and methods are described in the specification: [DOM Living Standard](https://dom.spec.whatwg.org).
>>>>>>> 193319c963b9ba86ac7d9590f7261a36ecdcc4d2

```smart header="DOM ਸਿਰਫ ਬ੍ਰਾਜ਼ਰਾਂ ਲਈ ਨਹੀਂ ਹੈ"
DOM ਨਿਰਧਾਰਨ ਦਸਤਾਵੇਜ਼ ਦੇ ਢਾਂਚੇ ਬਾਰੇ ਦੱਸਦਾ ਹੈ ਅਤੇ ਪ੍ਰਦਾਨ ਕਰਦਾ ਹੈ objects ਇਸ ਨੂੰ ਫੇਰਬਦਲ ਕਰਨ ਲਈ. ਇੱਥੇ ਗੈਰ ਬ੍ਰਾਜ਼ਰ ਉਪਕਰਣ ਹਨ ਜੋ DOM ਦੀ ਵਰਤੋਂ ਵੀ ਕਰਦੇ ਹਨ.

ਉਦਾਹਰਣ ਦੇ ਲਈ, ਸਰਵਰ-ਸਾਈਡ ਸਕ੍ਰਿਪਟ ਜੋ HTML ਪੇਜਾਂ ਨੂੰ ਡਾਉਨਲੋਡ ਕਰਦੀਆਂ ਹਨ ਅਤੇ ਉਹਨਾਂ ਤੇ ਪ੍ਰਕਿਰਿਆ ਕਰਦਿਆਂ ਹਨ ਵੀ DOM ਦੀ ਵਰਤੋਂ ਕਰ ਸਕਦੀਆਂ ਹਨ. ਉਹ ਹਾਲਾਂਕਿ ਨਿਰਧਾਰਨ ਦੇ ਸਿਰਫ ਇੱਕ ਹਿੱਸੇ ਦਾ ਸਮਰਥਨ ਕਰ ਸਕਦੇ ਹਨ.
```

```smart header="CSSOM for styling"
<<<<<<< HEAD
CSS ਨਿਯਮ ਅਤੇ ਸਟਾਈਲਸ਼ੀਟ HTML ਤੋਂ ਵੱਖਰੇ ਢੰਗ ਨਾਲ ਬਣੀਆਂ ਹੋਈਆਂ ਹਨ. ਇਸ ਲਈ ਇੱਕ ਵੱਖਰਾ ਨਿਰਧਾਰਨ ਹੈ, [CSS Object Model (CSSOM)](https://www.w3.org/TR/cssom-1/), ਇਹ ਦੱਸਦਾ ਹੈ ਕਿ ਉਹਨਾਂ ਨੂੰ ਕਿਵੇਂ ਇਕਾਈ ਵਜੋਂ ਦਰਸਾਇਆ ਜਾਂਦਾ ਹੈ, ਅਤੇ ਉਹਨਾਂ ਨੂੰ ਕਿਵੇਂ ਪੜ੍ਹਨਾ ਅਤੇ ਲਿਖਣਾ ਹੈ.

CSSOM ਜਦੋਂ ਅਸੀਂ ਦਸਤਾਵੇਜ਼ ਲਈ ਸ਼ੈਲੀ ਦੇ ਨਿਯਮਾਂ ਨੂੰ ਸੰਸ਼ੋਧਿਤ ਕਰਦੇ ਹਾਂ ਤਾਂ DOM ਦੇ ਨਾਲ ਮਿਲ ਕੇ ਵਰਤਿਆ ਜਾਂਦਾ ਹੈ.ਅਭਿਆਸ ਵਿੱਚ ਹਾਲਾਂਕਿ, CSSOM ਦੀ ਬਹੁਤ ਘੱਟ ਲੋੜ ਹੁੰਦੀ ਹੈ, ਕਿਉਂਕਿ ਆਮ ਤੌਰ ਤੇ CSS ਨਿਯਮ ਸਥਿਰ ਹੁੰਦੇ ਹਨ. ਸਾਨੂੰ ਜਾਵਾ ਸਕ੍ਰਿਪਟ ਤੋਂ ਸੀ ਐੱਸ ਐੱਸ ਦੇ ਨਿਯਮਾਂ ਨੂੰ ਜੋੜਨ / ਹਟਾਉਣ ਦੀ ਬਹੁਤ ਘੱਟ ਲੋੜ ਹੈ, ਪਰ ਇਹ ਵੀ ਸੰਭਵ ਹੈ.
=======
There's also a separate specification, [CSS Object Model (CSSOM)](https://www.w3.org/TR/cssom-1/) for CSS rules and stylesheets, that explains how they are represented as objects, and how to read and write them.

CSSOM is used together with DOM when we modify style rules for the document. In practice though, CSSOM is rarely required, because we rarely need to modify CSS rules from JavaScript (usually we just add/remove CSS classes, not modify their CSS rules), but that's also possible.
>>>>>>> 193319c963b9ba86ac7d9590f7261a36ecdcc4d2
```

## BOM (ਬਰਾਜ਼ਰ ਆਬਜੈਕਟ ਮਾਡਲ)

ਬ੍ਰਾਜ਼ਰ ਆਬਜੈਕਟ ਮਾਡਲ (ਬੀਓਐਮ) ਦਸਤਾਵੇਜ਼ ਨੂੰ ਛੱਡ ਕੇ ਸਭ ਕੁਝ ਦੇ ਨਾਲ ਕੰਮ ਕਰਨ ਲਈ ਬ੍ਰਾਜ਼ਰ (ਮੇਜ਼ਬਾਨ ਵਾਤਾਵਰਣ) ਦੁਆਰਾ ਪ੍ਰਦਾਨ ਕੀਤੇ ਵਾਧੂ ਆਬਜੈਕਟ ਨੂੰ ਦਰਸਾਉਂਦਾ ਹੈ.

ਉਦਾਹਰਣ ਦੇ ਲਈ:

- [navigator](mdn:api/Window/navigator) ਆਬਜੈਕਟ ਬ੍ਰਾਜ਼ਰ ਅਤੇ ਓਪਰੇਟਿੰਗ ਸਿਸਟਮ ਬਾਰੇ ਬੈਕਗ੍ਰਾਉਂਡ ਦੀ ਜਾਣਕਾਰੀ ਪ੍ਰਦਾਨ ਕਰਦਾ ਹੈ.ਇਸ ਦੀਆਂ ਬਹੁਤ ਸਾਰੀਆਂ properties ਹਨ, ਪਰ ਦੋ ਸਭ ਤੋਂ ਵੱਧ ਜਾਣੇ ਜਾਂਦੇ ਹਨ: `navigator.userAgent` -- ਮੌਜੂਦਾ ਬ੍ਰਾਜ਼ਰ ਬਾਰੇ, ਅਤੇ `navigator.platform` -- ਪਲੇਟਫਾਰਮ ਬਾਰੇ (ਵਿੰਡੋਜ਼ / ਲੀਨਕਸ / ਮੈਕ ਆਦਿ ਵਿੱਚ ਅੰਤਰ ਕਰਨ ਵਿੱਚ ਸਹਾਇਤਾ ਕਰ ਸਕਦਾ ਹੈ).
- [location](mdn:api/Window/location) ਆਬਜੈਕਟ ਸਾਨੂੰ ਮੌਜੂਦਾ ਯੂਆਰਐਲ ਨੂੰ ਪੜ੍ਹਨ ਦੀ ਆਗਿਆ ਦਿੰਦਾ ਹੈ ਅਤੇ ਬ੍ਰਾਜ਼ਰ ਨੂੰ ਨਵੇਂ 'ਤੇ ਭੇਜ ਸਕਦਾ ਹੈ.

ਇੱਥੇ ਅਸੀਂ ਕਿਵੇਂ `location` object ਹੇਠ ਲਿਖੇ ਅਨੁਸਾਰ ਇਸਤੇਮਾਲ ਕਰ ਸਕਦੇ  ਹਾਂ :

```js run
alert(location.href); // ਮੌਜੂਦਾ URL ਵੇਖਾਉਦਾ ਹੈ
if (confirm("Go to Wikipedia?")) {
  location.href = "https://wikipedia.org"; // ਬਰਾਜ਼ਰ ਨੂੰ ਯੂਆਰਐਲ ਤੇ ਭੇਜੋ
}
```

ਫੰਕਸ਼ਨ `alert/confirm/prompt` ਵੀ BOM ਇੱਕ ਹਿੱਸਾ ਹਨ : ਉਹ ਸਿੱਧੇ ਦਸਤਾਵੇਜ਼ ਨਾਲ ਸਬੰਧਤ ਨਹੀਂ ਹਨ, ਪਰ ਉਪਭੋਗਤਾ ਨਾਲ ਸੰਚਾਰ ਕਰਨ ਦੇ ਸ਼ੁੱਧ ਬ੍ਰਾਜ਼ਰ ਤਰੀਕਿਆਂ ਨੂੰ ਦਰਸਾਉਂਦੇ ਹਨ.

```smart header="Specifications"
BOM ਜਨਰਲ ਦਾ ਹਿੱਸਾ ਹੈ [HTML specification](https://html.spec.whatwg.org).

ਹਾਂ, ਤੁਸੀਂ ਇਹ ਸਹੀ ਸੁਣਿਆ ਹੈ. ਤੇ HTML ਐਕਸਚੇਜ਼<https://html.spec.whatwg.org> ਸਿਰਫ "HTML ਭਾਸ਼ਾ" ਬਾਰੇ ਨਹੀਂ(tags, attributes), ਪਰ ਇਹ ਇੱਕ ਸਮੂਹ ਨੂੰ ਕਵਰ ਕਰਦਾ ਹੈ objects, methods ਅਤੇ ਬ੍ਰਾਜ਼ਰ-ਸੰਬੰਧੀ DOM ਐਕਸਟੈਂਸ਼ਨਾਂ. ਇਹ "ਵਿਆਪਕ ਸ਼ਬਦਾਂ ਵਿੱਚ HTML" ਹੈ.ਨਾਲ ਹੀ, ਕੁਝ ਹਿੱਸਿਆਂ 'ਤੇ ਸੂਚੀਬੱਧ ਵਾਧੂ specifications ਹਨ <https://spec.whatwg.org>.
```

## ਸਾਰ

ਮਾਪਦੰਡਾਂ ਬਾਰੇ ਗੱਲ ਕਰਦਿਆਂ, ਸਾਡੇ ਕੋਲ ਹੈ:

DOM ਨਿਰਧਾਰਨ
: ਦਸਤਾਵੇਜ਼ ਦੇ ਢਾਂਚੇ, ਹੇਰਾਫੇਰ ਅਤੇ ਘਟਨਾਵਾਂ ਬਾਰੇ ਦੱਸਦਾ ਹੈ, ਵੇਖੋ <https://dom.spec.whatwg.org>.

CSSOM ਨਿਰਧਾਰਨ
: ਸਟਾਈਲਸ਼ੀਟ ਅਤੇ ਸ਼ੈਲੀ ਦੇ ਨਿਯਮਾਂ, ਉਹਨਾਂ ਨਾਲ ਹੇਰਾਫੇਰ ਅਤੇ ਉਹਨਾਂ ਨੂੰ ਦਸਤਾਵੇਜ਼ਾਂ ਨਾਲ ਜੋੜਨ ਬਾਰੇ ਦੱਸਦਾ ਹੈ, ਵੇਖੋ <https://www.w3.org/TR/cssom-1/>.

HTML ਨਿਰਧਾਰਨ
: HTML ਭਾਸ਼ਾ (ਉਦਾ. ਟੈਗਸ) ਅਤੇ ਬੀਓਐਮ (ਬ੍ਰਾਜ਼ਰ ਆਬਜੈਕਟ ਮਾਡਲ) ਦਾ ਵਰਣਨ ਕਰਦਾ ਹੈ --ਵੱਖ ਵੱਖ ਬਰਾਜ਼ਰ ਫੰਕਸ਼ਨ: `setTimeout`, `alert`, `location` ਅਤੇ ਇਸ ਤਰਾਂ ਹੋਰ, ਦੇਖੋ <https://html.spec.whatwg.org>. ਇਹ DOM ਨਿਰਧਾਰਨ ਲੈਂਦਾ ਹੈ ਅਤੇ ਇਸਨੂੰ ਬਹੁਤ ਸਾਰੀਆਂ ਵਾਧੂ ਵਿਸ਼ੇਸ਼ਤਾਵਾਂ ਅਤੇ ਵਿਧੀਆਂ ਨਾਲ ਵਧਾਉਂਦਾ ਹੈ.

ਇਸ ਤੋਂ ਇਲਾਵਾ, ਕੁਝ ਕਲਾਸਾਂ ਦਾ ਵੱਖਰੇ ਤੌਰ ਤੇ ਵਰਣਨ ਕੀਤਾ ਜਾਂਦਾ ਹੈ <https://spec.whatwg.org/>.

ਕਿਰਪਾ ਕਰਕੇ ਇਨ੍ਹਾਂ ਲਿੰਕਾਂ ਨੂੰ ਨੋਟ ਕਰੋ, ਕਿਉਂਕਿ ਇੱਥੇ ਸਿੱਖਣ ਲਈ ਬਹੁਤ ਸਾਰੀਆਂ ਚੀਜ਼ਾਂ ਇਸ ਨੂੰ ਚੇਕ ਕਰਨਾ ਅਤੇ ਸਭ ਕੁਝ ਯਾਦ ਰੱਖਣਾ ਅਸੰਭਵ ਹੈ.

ਜਦੋਂ ਤੁਸੀਂ ਕਿਸੇ property ਜਾਂ ਕਿਸੇ method ਬਾਰੇ ਪੜ੍ਹਨਾ ਚਾਹੁੰਦੇ ਹੋ, ਤਾਂ ਮੋਜ਼ੀਲਾ ਮੈਨੂਅਲ ਐੱਨ <https://developer.mozilla.org/en-US/search> ਇਹ ਇਕ ਵਧੀਆ ਸਰੋਤ ਵੀ ਹੈ, ਪਰ ਅਨੁਸਾਰੀ ਵਿਸ਼ੇਸ਼ ਬਿਹਤਰ ਹੋ ਸਕਦੀ ਹੈ: ਇਹ ਵਧੇਰੇ ਗੁੰਝਲਦਾਰ ਅਤੇ ਪੜ੍ਹਨ ਲਈ ਲੰਮੀ ਹੈ, ਪਰ ਇਹ ਤੁਹਾਡੇ ਬੁਨਿਆਦੀ ਗਿਆਨ ਨੂੰ ਵਧੀਆ ਅਤੇ ਸੰਪੂਰਨ ਬਣਾ ਦੇਵੇਗਾ..

ਕੁਝ ਲੱਭਣ ਲਈ, ਇੰਟਰਨੈਟ ਦੀ ਵਰਤੋਂ ਕਰਨਾ ਅਕਸਰ ਟੁਕਵਾ ਹੁੰਦਾ ਹੈ "WHATWG [term]" or "MDN [term]", e.g <https://google.com?q=whatwg+localstorage>, <https://google.com?q=mdn+localstorage>.

ਹੁਣ ਅਸੀਂ DOM ਸਿੱਖਣ ਲਈ ਉਤਰਾਂਗੇ, ਕਿਉਂਕਿ ਏਹ ਦਸਤਾਵੇਜ਼ UI ਵਿਚ ਕੇਂਦਰੀ ਭੂਮਿਕਾ ਅਦਾ ਕਰਦਾ ਹੈ.
