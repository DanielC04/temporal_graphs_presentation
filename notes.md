# presentation notes

## before introduction
- ever taken a graph course: street maps big motivational example
- i thought: give me big servers and 1000 years & i can build google maps!
- But: bus, tram and trains aren't waiting for you!
- go home now: takes longer, than going home in 10 minutes
-> time changes something about the route that I take
-> deeper: time changes the graph representation of city
- questions emerge
  - what exactly does time change?
  - how could we model this change?
  - do our normal algorithms work?

## Motivation
### clip school day
- show clip
- french researchers: put RFID on everybody in a school
-> track proximity & social interactions
- only info:
  - who is teacher/student
  - proximity every x minutes
  - class mates
- visualization possible
- why interesting? INCREDICBLE story telling
- temporal graph rich in information
- studying this: insights in 

### Google maps
- what does google maps use temporal data for:
  - account for traffic
  - road closures
  - transit schedules
- e.g. Bus departs in 15 mins
  -> travel distance of bus depends on departure
  -> some connections might not exist at some points in time
- pretend for now: modified Dijkstra/A* is used for shortest path calculations (heuristic for A* takes both spatial as well as temporal information into account)

### Distributed systems
- many applications: rely on large p2p (peer to peer) systems
-> prone to errors
- availability of distributed resources 
  -> e.g. server might fail at some point in time or have throttled bandwidth
-> should adapt to changes with:
  - self organization
  - self healing
  - self adaption
- temporal reachability queries
- or: study some properties that hold under any circumstance (e.g. small temporal diameter, ...)

### for physical/chemical model
- real-world temporal changes can be modeled with temporal graphs
- paper: how do chemicals react in dissolved organic matter !?
- no more questions xD

### How to (visually) represent temporal graphs
- normal graphs: strong representation
- dilemma: how to show the third (temporal) dimension?
- research topic
- some ideas in pictures
  1. flow of time symbolized horizontal axis
  2. edge labels (more about that later)
  3. actual passage of time
  4. 3 dimensional drawing -> here: domain-specific

## How to model temporal graphs
- static graph G = (V, E) where every edge is labeled with 0 or more natural numbers
- labels correspond to time steps (-> seconds, days, months; when each edge is available)
  -> more general: any discrete artificial measure of time

### labeled and temporal graphs
- first: take a step back
- labeled graph $G = (V, E, \lambda)$
- in general case: labels can be anything
- NOW: temporal graphs
  -> no labels for vertices
  -> Z is set of natural numbers (2^N)
- why on one slide? -> closely related
- interpretation of labeled graph as temporal graph possible and vice versa
- e.g. proper edge-labeling
- looks trivial, but has deeper meaning!
- no 2 edges appear at same time
- exercise!!!

### Transitivity of reachability in static graphs
- not my only proof, i swear :)
- no rigeous proof, but rather intuition
- please ignore that we haven't defined reachability exactly yet and use the analogue of reachability on static graphs

-> not transitive
- what can we learn from this?
- fundamental structural differences between static and temporal graphs
- ideas and algorithms that rely on transitivity of reachability in static graphs might not work in temporal graphs
- 

### Second notation
- time edges
- exercise!!!

### static expansion of graphs
- notion of storing separate graph per time step
- advantages:
  - use existing algorithms
  - simple representation (both visually and computationally)
  - in real life: speed up by parallelization
- disadvantages:
  - memory consumption/graph size: $|V| \cdot \alpha(\lambda) $
  - redundant information
  - doesn't scale to high temporal resolution

### journeys
- nearly last basic concept we'll cover
- first: repeat path in static graph
- walk is a finite/infinite sequence of edges
- path is a walk where all vertices are distinct
  -> note: therefore also all edges are distinct

- central concept -> also exists on temporal graphs
