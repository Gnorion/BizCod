# Graph Abstract Data Type

A graph data structure consists of a finite (and possibly mutable) set of vertices (also called nodes or points), together with a set of unordered pairs of these vertices for an undirected graph or a set of ordered pairs for a directed graph. These pairs are known as edges (also called links or lines), and for a directed graph are also known as edges but also sometimes arrows or arcs. The vertices may be part of the graph structure, or may be external entities represented by integer indices or references.

Here is a formal definition of Graph Data Type 

```js
    define model <graph-name> 
        vertices (Vertex)*
        edges (Edge)*
```

>MEP: So could the vertices be instances of various classes? Would they have to be all the same class or could they be arbitrary?
>
>MEP: I guess if the vertices were an `Interface` class then you could use any class that implements the interface.
>
>MEP: Here's what I'm thinking (not sure if my syntax is correct):

>MS: yes, it is correct. Vertex is a abstract class so any class that inherits from Vertex might be used
```js
    define model Facebook 
        vertices (Person)*
        edges (Friendship)*
        
    define model Person is Vertex
        name text
        
    Mike=Person.create(name='Mike')  
    Mary=Person.create(name='Mary') 
    G=Facebook()
    G.addVertex(Mike)
    G.addVertex(Mary)
    G.addEdge(Mike,Mary,10)
    G.addEdge(Mary,Mike,5)
```
A graph data structure may also associate to each edge some edge value, such as a symbolic label or a numeric attribute (cost, capacity, length, etc.).
The graph abstract data type (ADT) is defined as follows:

- Graph() creates a new, empty instance of graph.
- addVertex(vert) adds an instance of Vertex to the graph.
- addEdge(fromVert, toVert) Adds a new, directed edge to the graph that connects two vertices.
- addEdge(fromVert, toVert, weight) Adds a new, weighted, directed edge to the graph that connects two vertices.
- getVertex(vertKey) finds the vertex in the graph named vertKey.
- getVertices() returns the list of all vertices in the graph.
- it returns True for a statement of the form vertex in graph, if the given vertex is in the graph, False otherwise.

>MEP: What other functions might we have for doing interesting things with a graph?
>MEP: For example finding a spanning graph, or the shortest path between two vertices
>MEP: Or would we simply leave users to develop their own algorithms for these
>
>MEP: If the `Friendship` edge was defined like this
```js
    define model Friendship 
        dateStarted date
        dateEnded date
        duration number
```

>MEP: Would we be able to do something like this?
```js
    G.getVertex(Mike.name).dateStarted=currentDate
```

>MEP: There is a type for date. Is there also a type for time?
>
>MEP: I suppose we could even define the vertices of a graph to be `graphs` (essentially subgraphs)
>
>MEP: How would I add an edge that is `not` directed? Would I have to add it twice in each direction?
>
>MEP: When we add a vertex how are we defining/specifying its name?