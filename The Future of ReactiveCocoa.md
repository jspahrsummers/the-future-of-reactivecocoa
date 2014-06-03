# [fit] **The Future of**
# [fit] **ReactiveCocoa**
# @jspahrsummers

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

# [fit] _**Duals?**_
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

# **Push:**
## `Event -> ()`
## `() -> (Event -> ())`
# **Pull:**
## `() -> Event`
## `() -> (() -> Event)`

---

# [fit] Why is enumeration
# [fit] **blocking?**

---

# [fit] **Enumerator v2**
# [fit] `() -> Promise Event`

---

# **Push:**
## `Event -> ()`
## `() -> (Event -> ())`
# **Pull:**
## `() -> Promise Event`
## `() -> (() -> Promise Event)`

---

# [fit] Observables and Enumerables are:
# [fit] ✔︎ **Monadic**
# [fit] ✔︎ **Asynchronous**
# [fit] ✔︎ **Modular**
