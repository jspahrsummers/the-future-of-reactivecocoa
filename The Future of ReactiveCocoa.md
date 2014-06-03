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

# [fit] But why is enumeration
# [fit] **blocking**
# [fit] in a reactive framework?

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

# [fit] Promises allow work to be performed
# [fit] **_out-of-order_ & _asynchronously_**
# [fit] when and where the caller wants

---

# [fit] Observables and Enumerables are:
# [fit] ✔︎ **Monadic**
# [fit] ✔︎ **Modular**
# [fit] ✔︎ **Asynchronous**

---

# [fit] ~~Hot signals~~ **Observables**
# [fit] ~~Cold signals~~ **Enumerables**

---

# **Observables** are _always live_
# **Enumerables** _start new work_ with each enumeration

---

# **Observables** are the _same_ to all observers
# **Enumerables** are enumerated _independently_
