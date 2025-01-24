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

### for physical/chgemical model### for physical/chgemical modelss
- real-world temporal changes can be modeled with temporal graphs
- paper: how do chemicals react in dissolved organic matter !?
- no more questions 😆

### How to (visually) represent temporal graphs
- normal graphs: strong representation
- dilemma: how to show the third (temporal) dimension?
- research topic
- some ideas in pictures
  1. flow of time symbolized horizontal axis
  2. edge labels (more about that later)
  3. actual passage of time
  4. 3 dimensional drawing -> here: domain-specific



