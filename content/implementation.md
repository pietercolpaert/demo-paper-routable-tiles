## Implementation
{:#implementation}

### The Specification

Routable Tiles is a JSON-LD specification and the draft can be found at [https://openplanner.team/specs/2018-11-routable-tiles.html](https://openplanner.team/specs/2018-11-routable-tiles.html).
It has several aspects:

 1. It introduces a hypermedia specification reusing Hydra Collections for describing a tile server
 2. For a server to be compliant to routable tiles, nodes, ways and restrictions needs to be modeled.
 3. It introduces a mapping of the Open Street Map terms to an RDFS vocabulary

### The Ontology

The ontology is kept as a direct mapping from OSM terms to a Linked Data ontology. 
OSM terms are well-known among the developer community, 
which increases the adoption and facilitates the understanding of the ontology. 
Moreover, having an OSM ontology will allow other data providers 
to reuse the OSM terminology and thus link their datasets to OSM. An example:

We define 3 main classes: <code>osm:Way</code>, <code>osm:Relation</code> and <code>osm:Node</code>.
The <code>osm:members</code> property describes the members of the relation and the <code>osm:role</code> their function in the relation.
<code>osm:restriction</code> is used to model turn restrictions.

The property <code>osm:nodes</code> is used to link to an r<code>df:List</code> of <code>osm:Node</code> items.
In one page, multiple lists can be described.
If a Way crosses a tile, the other tile also mentioned the border Node in one of its rdf:Lists.
The property <code>osm:members</code> is used to link to an <code>rdf:List</code> of <code>osm:Member</code> items.

### The Server

The mapping scripts and server interface can be found at [https://github.com/openplannerteam/routeable-tiles](https://github.com/openplannerteam/routeable-tiles).
Every tile in Open Street Map on zoom level 14 is on the fly made available as JSON-LD.
Special attention was given to the HTTP server to include a server-side cache and to compress the HTTP response with gzip.
Furthermore, it sets both an etag header and a cache-control max-age header for client-side cache control.
Finally, it also allows webpages on other domains to request its data by setting the appropriate Cross Origin Resource Sharing headers.

<!--Due to [a recent change in the WhatWG fetch specification](https://github.com/whatwg/fetch/issues/862), there is also a need for supporting the OPTIONS method, that specifically allows all headers in its response.-->

For the URIs of Ways and Nodes, we decided to reuse the subject pages provided by the Open Street Map project itself.
We hope that at some point, Open Street Map decides to support a Linked Data representation on these URIs.
For example: [https://www.openstreetmap.org/node/366934331](https://www.openstreetmap.org/node/366934331) and [https://www.openstreetmap.org/way/242536619](https://www.openstreetmap.org/way/242536619).
