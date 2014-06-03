# [fit] **The Future of**
# [fit] **ReactiveCocoa**
# @jspahrsummers

---

# [fit] RAC 3.0

^ This was going to be a talk about what's been changing in RAC 3.0. Then I went to Lang.NEXT, and saw Erik Meijer–creator of Rx, upon which RAC is based—talk about duals and Rx, and it gave me a lot of crazy ideas.
^
^ This talk is now an attempt to pull the emergency brake, and give us a chance to Do Things Right™. But the central theme of RAC 3.0 will remain the same: simplicity.

---

# [fit] **Hot** _or_ **Cold?**

^ By far, the most confusing concept in RAC has been the distinction between “hot” and “cold” signals. A signal is “hot” if it's always live, or “cold” if it only starts doing something upon subscription.
^
^ Originally, RAC 3.0 “solved” this by encouraging cold signals everywhere. However, this complicates the terminology (why does “subscription” cause effects?), and it's a lie: signals of UI events—for example—are never truly cold.

---

# [fit] **.NET offers:**
# [fit] `IEnumerable`
# [fit] `IEnumerator`
# [fit] `IObservable`
# [fit] `IObserver`

^ .NET and Rx offer these four interfaces, corresponding to pull-driven and push-driven streams. Observables are what we would call “signals” in RAC.
^
^ Erik's talk focused specifically on how they relate to one another. Specifically, Enumerable and Observable are “duals.”

---

# [fit] **Observer**
# [fit] `Event -> ()`

^ Let's go over the types first. An observer (or subscriber, in RAC terms) performs side effects whenever an event is sent to it.

^ In Swift, this corresponds closely to the built-in `Sink` protocol.

---

# [fit] **Observable**
# [fit] `(Event -> ()) -> ()`

^ An observable (or signal, in RAC) accepts observers, and might perform side effects when they're attached.
^
^ So far, nothing too complicated.

---

# [fit] _**Duals?**_
# [fit] Flip the arrows!

^ You get the duals of the aforementioned interfaces if you simply flip the arrows around.

---

# [fit] **???**
# [fit] `() -> Event`

^ This is the dual of the Observer type. When invoked, it returns an event.

---

# [fit] **Enumerator**
# [fit] `() -> Event`

^ This matches a concept that we're already pretty familiar with: an enumerator returns things (events, in this case) when evaluated.
^
^ In Swift, this corresponds closely to the built-in `Generator` protocol.

---

# [fit] **Enumerable**
# [fit] `() -> (() -> Event)`

^ Likewise, if we flip the Observable type, we get an Enumerable. An enumerable (for example, a collection) can create enumerators.
^
^ In Swift, this correspond closely to the built-in `Sequence` protocol.

---

# **Push:**
## `Event -> ()`
## `(Event -> ()) -> ()`
# **Pull:**
## `() -> Event`
## `() -> (() -> Event)`

^ Putting it all together, we get these type signatures. Push-driven streams (observables/signals) on top, pull-driven streams (enumerables) on the bottom.
^
^ Pretty cool, right?

---

# [fit] But why is enumeration
# [fit] **blocking**
# [fit] in a reactive framework?

^ We've established the symmetry between observables and enumerables, but there's a problem with the Enumerator type…

---

# [fit] **Enumerator v1**
# [fit] `() -> Event`

^ Since the caller must get an Event, you can only retrieve values synchronously (by blocking the thread). That sucks.

---

# [fit] **Enumerator v2**
# [fit] `() -> Promise Event`

^ To retrieve values asynchronously, we can wrap each result in a promise, which will deliver the event to us at some point in the future.

---

# **Push:**
## `Event -> ()`
## `(Event -> ()) -> ()`
# **Pull:**
## `() -> Promise Event`
## `() -> (() -> Promise Event)`

^ As you can see, this kinda breaks the duality between observation and enumeration, but the benefit to responsiveness is definitely worth it.

---

# [fit] Promises allow work to be performed
# [fit] **_out-of-order_ & _asynchronously_**
# [fit] when and where the caller wants

^ It's not only about being non-blocking. If we wanted that, we could just use observables. Promises also allow the consumer to skip work or process events out-of-order.
^
^ For example, the consumer could immediately retrieve 5 promises, then realize it overcommitted, and get rid of the first 4 without having to ever start them. The consumer has complete control.

---

# [fit] Observables and Enumerables are:
# [fit] ✔︎ **Monadic**
# [fit] ✔︎ **Modular**
# [fit] ✔︎ **Asynchronous**

^ When they conform to these definitions, observables and enumerables become very powerful abstractions for stream manipulations and asynchrony.
^
^ The parallel Observer and Enumerator interfaces also improve modularity and extensibility, because they'll be satisfied with concrete implementations that make their own decisions about concurrency, processing order, etc.

---

# **Observables** are driven by the _producer_
# **Enumerables** are controlled by the _consumer_

^ Let's recap these guys.

---

# **Observables** are the _same_ to all observers
# **Enumerables** are enumerated _independently_

^ All observers of one observable see the same events simultaneously. Multiple enumerators may be based on the same enumerable, but can be at different points in the enumeration, and doing different things.

---

# **Observables** are _always live_
# **Enumerables** _start new work_ with each enumeration

^ Here's another way to say the same thing. Does this sound familiar?

---

# [fit] ~~Hot signals~~ **Observables**
# [fit] ~~Cold signals~~ **Enumerables**

^ Boom. Observables can completely replace hot signals, and enumerables can completely replace cold signals.
^
^ The type system helps us create a real distinction between the two, eliminating confusion and complexity.

---

# [fit] Questions?
