# [fit] **The Future of**
# [fit] **ReactiveCocoa**
# @jspahrsummers

---

* Hot?
* Cold?
* Lukewarm?

---

# [fit] ~~Subscriber~~ **Observer**
# [fit] ~~Signal~~ **Observable**

---

# [fit] **Observer**
# [fit] `Event -> ()`

---

# [fit] **Observable**
# [fit] `() -> (Event -> ())`

---

# [fit] **Duals**
# [fit] Flip the arrows!

---

# [fit] **???**
# [fit] `() -> Event`

---

# [fit] **Enumerator**
# [fit] `() -> Event`

---

# [fit] **Enumerable**
# [fit] `() -> (() -> Event)`

---

```haskell
() -> (Event -> ())

```

---

```haskell
() -> IO (Future (Event v))

Event v -> IO ()

Enumerable v -> Enumerator v
Enumerator v -> IO (Future (Event v))

Observable v -> Observer v -> Disposable
Observer v -> Event v -> IO ()
```

---

# Observable

---

# Enumerable

---

## Drag & Drop images

### Simply *drop an image onto the Deckset window* and the Markdown you need to display the image is automatically created and *copied to the clipboard.*

---

* This works with both local files and web images
* You don’t _have_ to drag the file, you can also type the Markdown yourself if you know how

![left,filtered](http://deckset-assets.s3-website-us-east-1.amazonaws.com/colnago1.jpg)
