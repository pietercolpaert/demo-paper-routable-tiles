## Implementation
{:#implementation}

Routable Tiles is a JSON-LD specification for which the working draft can be found at [https://openplanner.team/specs/2018-11-routable-tiles.html](https://openplanner.team/specs/2018-11-routable-tiles.html).
It has three main aspects: (i) it introduces a *hypermedia specification* reusing Hydra Collections for describing a tile server, (ii) a way to describe *Open Street Map’s nodes, ways and relations*; and (iii) it introduces a mapping of the Open Street Map basic terms to an RDFS vocabulary.

The Linked Geo Data vocabulary has been unavailable since 2018 and not updated since 2015.
Therefore we introduced our own vocabulary, that nonetheless takes a different approach.
Instead of mapping everything, we decided to map only the bare minimum needed specifically for the use case or route planing.
Therefore, we keep the ontology as close as possible to the actual OSM data model.
We added links to the appropriate Linked Geo Data classes (ontology has yet to be published, awaiting a third party implementation).

We define 3 main classes: *osm:Way*, *osm:Relation* and *osm:Node*.
The *osm:members* property describes the members of the relation and the *osm:role* their function in the relation.
*osm:restriction* is used to model turn restrictions.
The property *osm:nodes* is used to link to an *rdf:List* of *osm:Node* items.
In one page, multiple lists can be described.
If a Way crosses a tile, the other tile also mentioned the border Node in one of its rdf:Lists.
The property *osm:members* is used to link to an *rdf:List* of *osm:Member* items.

The mapping scripts and server interface can be found at [https://github.com/openplannerteam/routeable-tiles](https://github.com/openplannerteam/routeable-tiles).
Every tile in Open Street Map on zoom level 14 is on the fly made available as JSON-LD.
Special attention was given to the HTTP server to include a server-side cache and to compress the HTTP response with gzip.
Furthermore, it sets both an etag header and a cache-control max-age header for client-side cache control.
Finally, it also allows webpages on other domains to request its data by setting the appropriate Cross Origin Resource Sharing headers.

<!--Due to [a recent change in the WhatWG fetch specification](https://github.com/whatwg/fetch/issues/862), there is also a need for supporting the OPTIONS method, that specifically allows all headers in its response.-->

For the URIs of Ways and Nodes, we decided to reuse the subject pages provided by the Open Street Map project itself.
We hope that at some point, Open Street Map decides to support a Linked Data representation on these URIs.
For example: [openstreetmap.org/node/366934331](https://www.openstreetmap.org/node/366934331) and [openstreetmap.org/way/242536619](https://www.openstreetmap.org/way/242536619).
