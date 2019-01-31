## Implementation
{:#implementation}

### The Specification

Routable Tiles is a JSON-LD specification and the draft can be found at [https://openplanner.team/specs/2018-11-routable-tiles.html](https://openplanner.team/specs/2018-11-routable-tiles.html)
It has several aspects:

 1. It introduces a hypermedia specification reusing Hydra Collections for describing a tile server
 2. For a server to be compliant to routable tiles, nodes, ways and restrictions needs to be modeled.
 3. It introduces a mapping of the Open Street Map terms to an RDFS vocabulary

#### Hypermedia

While in the geospatial world, standards such as WMS, WFS, ... seek for strict contracts between servers and agents,
in the Linked Open Data world, hypermedia controls are used to express what building blocks are supported by the server.
From every document, another document can be reached by interpreting the metadata.
Intelligent agents crawl over this data in order to find answers to queries.

<figure class="" id="listing1">
<code>
<pre>
{
  "@id": "«currentPageURL»",
  "tiles:zoom": 14,
  "tiles:longitudeTile": 8398,
  "tiles:latitudeTile": 5463,
  "dcterms:isPartOf": {
    "@id": "https://tiles.openplanner.team/planet",
    "@type": "hydra:Collection",
    "dcterms:license":
            "http://opendatacommons.org/licenses/odbl/1-0/",
    "dcterms:rights":
            "http://www.openstreetmap.org/copyright",
    "hydra:search": {
      "@type": "hydra:IriTemplate",
      "hydra:template": "https://tiles.openplanner.team/14/{x}/{y}",
      "hydra:variableRepresentation": "hydra:BasicRepresentation",
      "hydra:mapping": [
        {
          "@type": "hydra:IriTemplateMapping",
          "hydra:variable": "x",
          "hydra:property": "tiles:longitudeTile",
          "hydra:required": true
        },
        {
          "@type": "hydra:IriTemplateMapping",
          "hydra:variable": "y",
          "hydra:property": "tiles:latitudeTile",
          "hydra:required": true
        }
      ]
    }
  },
  "@graph" : [ ... <a href="#the-ontology">other data</a> ... ]
}
</pre>
</code>
<figcaption>Example implementation of the routable tiles hypermedia: the description of the tile is given, as well as a search form in a hydra:Collection with a URL template well-known in the geospatial world. For the @context, see the full specification at https://openplanner.team/specs/2018-11-routable-tiles.html</figcaption>
</figure>

### The Ontology

The ontology is kept as a direct mapping from OSM terms to a Linked Data ontology. An example:

<figure class="" id="code-example-nodes-ways">
<code>
<pre>
{
  "@context" : {
     ... <a href="#hypermedia">See section on hypermedia</a>...
  },
  "@graph": [
    {
      "@id": "#Way1",
      "@type": "osm:Way",
      "rdfs:label": "Chaussée de Haecht - Haachtsesteenweg",
      "osm:maxspeed": "30",
      "osm:highway": "osm:tertiary",
      "osm:nodes" : [ "#Node1", "#Node2" ]
    },
    {
      "@id": "#Node1",
      "geo:long": 3.14,
      "geo:lat": 51.2
    },
    {
      "@id": "#Node2",
      "geo:long": 3.12,
      "geo:lat": 51.32
      "osm:barrier": "osm:bollard"
      "osm:foot": "osm:yes"
      "osm:bicycle": "osm:yes"
    },
    {
      "@id": "#Node3",
      "geo:long": 3.22,
      "geo:lat": 51.22
    },
    {
      "@id": "#Way2",
      "@type": "osm:Way",
      "rdfs:label": "Rue Cornet de Grez - Cornet de Grezstraat",
      "osm:highway": "osm:residential",
      "osm:oneway": "yes",
      "osm:oneway-bicycle": "no",
      "osm:highway": "osm:tertiary",
      "osm:nodes" : [ "#Node1", "#Node3" ]
    },
    {
      "@id": "#TurnRestriction1",
      "@type": "osm:Relation",
      "osm:restriction":"osm:no_right_turn",
      "osm:from": "#Way1",
      "osm:to": "#Way2",
      "osm:via": "#Node1"
    }
  ]
}
  </pre>
</code>
<figcaption>An example of two  Ways, a couple of Nodes, one containing a bollard, and a restriction to turn right.</figcaption>
</figure>

We define 3 main classes: osm:Way, osm:Relation and osm:Node.
  
osm:from, osm:to and osm:via are predicates to indicate how a Relation maps Ways and Nodes.

osm:restriction is used to model turn restrictions. There are <a href="https://wiki.openstreetmap.org/wiki/Relation:restriction">9 possibilities as a range</a>:

 1. osm:no\_left_turn
 2. osm:no\_right_turn
 3. osm:no\_straight_on
 4. osm:no\_u_turn
 5. osm:only\_right_turn
 6. osm:only\_left_turn
 7. osm:only\_straight\_on
 8. osm:no\_entry
 9. osm:no\_exit

The property osm:nodes is used to link to an rdf:List of osm:Node items.
In one page, multiple lists can be described.
If a Way crosses a tile, the other tile also mentioned the border Node in one of its rdf:Lists.

### The Server

The mapping scripts and server interface can be found at [https://github.com/openplannerteam/routeable-tiles](https://github.com/openplannerteam/routeable-tiles).
Every tile in Open Street Map on zoom level 14 is on the fly made available as JSON-LD.
Special attention was given to the HTTP server to include a server-side cache and to compress the HTTP response with gzip.
Furthermore, it sets both an etag header and a cache-control max-age header for client-side cache control.
Finally, it also allows webpages on other domains to request its data by setting the appropriate Cross Origin Resource Sharing headers.

For the URIs of Ways and Nodes, we decided to reuse the subject pages provided by the Open Street Map project itself.
We hope that at some point, Open Street Map decides to support a Linked Data representation on these URIs.
For example: [https://www.openstreetmap.org/node/366934331](https://www.openstreetmap.org/node/366934331) and [https://www.openstreetmap.org/way/242536619](https://www.openstreetmap.org/way/242536619).
