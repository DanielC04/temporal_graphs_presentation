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
- why interesting? INCREDIBLE story telling
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
  - self organization/adaptation
  - self healing
- temporal reachability queries
- or: study some properties that hold under any circumstance (e.g. small temporal diameter, ...)

### for physical/chemical model
- real-world temporal changes can be modeled with temporal graphs
- paper: how do chemicals react in dissolved organic matter !?
- no more questions xD

### dissemination processes
- How does information, a disease, behaviour, ... spread over time in a network?
- corona pandemics -> determine bottlenecks, who to vaccinate and accelerators
- identify critical times and nodes
- e.g. social media: understand spread of viral hashtag


## How to model temporal graphs

### How to (visually) represent temporal graphs
- normal graphs: strong representation
- side note: I name 'normal' graphs static graphs from now on
- dilemma: how to show the third (temporal) dimension?
  -> assume discrete time steps for now
  -> some edges are only present during specific time steps
- research topic
- some ideas in pictures
  1. flow of time symbolized horizontal axis
  2. edge labels (more about that later)
     - static graph G = (V, E) where every edge is labeled with 0 or more natural numbers
      - labels correspond to time steps (-> seconds, days, months; when each edge is available)
        -> more general: any discrete artificial measure of time
  3. actual passage of time
  4. 3 dimensional drawing -> here: domain-specific
 
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
  - memory consumption/graph size: $|V| \cdot \alpha(\lambda)$
  - redundant information
  - doesn't scale to high temporal resolution

### journeys
- nearly last basic concept we'll cover
- first: repeat path in static graph
- walk is a finite/infinite sequence of edges
- path is a walk where all vertices are distinct
  -> note: therefore also all edges are distinct

- central concept -> also exists on temporal graphs

### computing the foremost journey
- problem statement:
  - given source node s and a start time $t$ compute the foremost s-w journey for all $w \in V$

## dissemination processes
- never seen such a funny start of a paper section
- deep down mathematicians are just gossips lol
 
### what processes exist?
- spread of information, rumor, fake news, disease, ...
- commonly studied:
  - spread research findings
  - spread information or maybe even ad campaign in a social network
  - spread of diseases in communities
- things that are studied (in the more traditional setting of dissemination):
    - source of information
    - medium of spread -> social network, publications
    - timing
- has been shown shown that underlying network structure can strongly affect dynamic processes -> big difference to analysis of static graph
- network structure affects speed and extent of spreading
----
- now, very concrete use case: vaccination problem
 
### vaccination problem
- refers to challenge of effectively planning and executing vaccination campaigns
- we focus on theoretical analysis of temporal network to identify critical nodes and times
- assumption: there are individuals who, through their behavior, are more likely than average to become infected and to spread the disease
further
- key questions include:
  - who should be vaccinated first? -> corona: old people and personal that is critical for infrastructure, health system
  - How can we minimize the spread of the disease? -> open up, but when?
  - What role does timing play in vaccination strategy? -> how should vaccination be prioritized?
- already know basic terms: but overall goal: herd immunity
- herd immunity: occurs when a large enough fraction $f$ of a community is immune to disease, thus limiting its ability to spread
  -> lower f by strategically vaccinating people in risk

### vaccination problem - more technical problem statement
- How can we optimally choose a fraction $f$ of a population to vaccinate using only local information?
  - optimally: economically? mortality? DALYs (Disability adjusted life years)?
  - vaccinate: instant and 100% effective
  - local information: query nodes about information about neighbors but not more
 
### Neighbourhood vaccination protocol
> choose a person at random among all persons that have been involved in at least one contact at time t*, ask her to name someone she met, vaccinate this other person, and repeat until a desired fraction of the vertices are vaccinated
- talk through example
- important properties of vaccination protocol
  - only uses local information
- why is it good?
  - sample people in proportion to their degree
  - importance of person is proportional to $deg^2$
    - infection rate ~ degree
    - spreading rate (once infected) ~ degree

### Modelling dissemination processes with temporal graphs
- nodes represent individuals, groups or organizations
- edges represent interactions
- time labels represent the time of interaction
- for now: interactions are all of equal, very short length
- example: could be the truly underlying graph of static example earlier

### The infection process
- new type of temporal graph representation:
  - basically static expansion of temporal graph
  - every row is one person
  - x-axis: time
  - vertical lines represent contact
- split given data into two parts:
1. learning period
- then: vaccinate (instantaneously) and disease starts at one source node
2. simulate spreading of disease with SIS (Susceptible-infected-susceptible) simulations
   - two groups: either susceptible or infected
   - we assume: infected stay infected, since our simulation time is very short








