##  Conclusion and discussion
{:#conclusion}

In this paper, we introduced a specification for publishing Open Street Map’s roads as Linked Open Data following the ideas behind [Linked Data Fragments](cite:cites tpf).
We conclude with a list of benefits and open issues on this approach.

Firstly, the server costs are lower as it does not have to answer any individual routing request.
Instead it sends the data itself to the client that needs to perform the algorithm itself.
The URLs that are requested are the same thanks to the hypermedia controls and HTTP caching can be leveraged.
Next to the fact that server-costs become limited, it also gives flexibility to developers using the data.
They do not have to contact the server-administrators of these open datasets for new features to add.
Just like vector tiles styling, they can tailor the routing algorithm to their end-user needs in the browser.
 
This also gives the benefit that not one server has to contain all of the world’s data.
It opens the door to use cases where source selection also happens on the client and multiple sources are queried at once.
Also for use cases outside the routing domain, routable tiles becomes useful.
The hypermedia controls can be added as an [actor to Comunica (future work for now)](cite:cites taelman_iswc_2018) and help it solve geospatial queries over any data source by downloading only the right tiles.

A precondition in order to be queryable by Comunica, is that the data is available in an RDF serialization.
As we use JSON-LD with well thought-out context, this data can be serialized into usable RDF.
However, an open issue is still whether the Linked Data model as such is useful.
For example, when another source wants to do a statement about a part of a road that is not yet an osm:Way instance, how will this data be interoperable with this dataset?

In future work, we will benchmark the different in size and performance between Valhalla tiles (protobuf) and Routable Tiles (JSON-LD + gzip).
Maybe there will be a need in the future for routable tiles specification that supports a binary format in order to reduce size.

In  general, still a lot of optimizations can be done, such as applying contraction hierarchies and exposing data on multiple zoom levels.

