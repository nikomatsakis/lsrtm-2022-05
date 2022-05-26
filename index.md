class: center
name: title
count: false

# LSRTM 2022-05

.p60[![Ferris](./images/ferris.svg)]

.left[.citation[View slides at `https://nikomatsakis.github.io/lsrtm-2022-05/`]]

---

# JavaScript promises

```js
async function process() {
    let promise = sendRequest();
    let result = await promise;
}

async function sendRequest() { /* ... */ }
```

![JavaScript promise timeline](images/js-promise.drawio.svg)

???

---

# Rust futures

```rust
async fn process() {
    let future = sendRequest();
    let result = future.await;
}

async fn sendRequest() -> Result { /* ... */ }
```

![Rust promise timeline](images/rust-promise.drawio.svg)

---

# Rust futures 1

```rust
async fn process() {
    let future = sendRequest();
    let result = future.await;
}

async fn sendRequest() -> Result { /* ...1 */ }
```

.line2[![Arrow](./images/Arrow.png)]

![Rust promise timeline](images/rust-promise-step-1.drawio.svg)

---

# Rust futures 2

```rust
async fn process() {
    let future = sendRequest();
    let result = future.await;
}

async fn sendRequest() -> Result { /* ...2 */ }
```

.line3[![Arrow](./images/Arrow.png)]

![Rust promise timeline](images/rust-promise-step-2.drawio.svg)

---

# Rust future combinators

```rust
use futures::future;

async fn process() {
    let future1 = sendRequest();
    let future2 = sendRequest();
    let future3 = future::join(future1, future2);
    let (result1, result2) = future3.await;
}

async fn sendRequest() -> Result { /* ... */ }
```

![Rust combinator timeline](images/rust-combinator.drawio.svg)

--

.line1[![Arrow](./images/Arrow.png)]

You can add arrows like this!