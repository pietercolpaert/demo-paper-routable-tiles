##  Conclusion and future work
{:#conclusion}

This demo introduced a tiling mechanism for publishing road networks in Linked Data.
Compared to a SPARQL endpoint approach or server answering any individual route planning request,
the server costs in our approach are indisputably lower.
Thanks to the hypermedia controls, the full dataset can be automatically discovered, and HTTP caching can be leveraged.
Furthermore, developers of route planning application are given more flexibility as they are now in full control of the algorithm.
Just like vector tiles styling, they can tailor the routing algorithm to their end-user needs in the browser.
This also opens the door to use cases where multiple sources are queried at once.

Nevertheless, it still remains an open question if applying this kind of Linked Data model/HTTP URIs
to the roads related data is the optimal approach.
For example, when another source wants to do a statement 
about a part of a road, chances are low it is already available as a separate osm:Way instance, and thus the source data would have to be altered to split the original entity into two.

In future work, we will benchmark the difference in size and performance 
between Valhalla tiles (protobuf) and Routable Tiles (JSON-LD + gzip).
Maybe there will be a need in the future for the Routable Tiles specification 
to support a binary format in order to reduce size. 
In general, still several other optimizations can be done, 
such as applying summaries over different zoom levels.
In order to achieve better adoption of the hypermedia controls,
an [actor will be added to the Linked Data query agent called Comunica](cite:cites taelman_iswc_2018).
This way, we will help to solve geo-spatial queries over any data source by downloading only the right tiles even beyond road networks.
