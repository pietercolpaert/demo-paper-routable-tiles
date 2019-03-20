## Related work
{:#sota}

### Geospatial data on the Web

[Spatial Data on the Web](cite:cites sdw) is a W3C and OGC collaboration 
to create a list of best practices for spatial data on the Web.
It takes a strong position in favor of HTTP URIs to identify resources.
The rationale is that Linked Data principles such as the use of HTTP URIs as global identifiers, 
raises the interoperability of geo-spatial datasets 
by providing a common set of semantics that can be reused by data publishers.
 
Slippy maps are maps often included in web-pages on which you can pan around.
In order to reduce server load, the client is preconfigured with a URL template of the web-server containing image tiles.
E.g., <code>https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png</code>, where <code>s</code> denotes a subdomain to be used, <code>z</code> the zoom-level the slippy map is at, and <code>x</code> and <code>y</code> are the coordinates of the upper left corner of the tile.
When the map is loaded, the client can calculate all URLs necessary.
Vector tiles reuse this idea to, instead of raster images, publish the raw data behind the tiles.
The client can then render the maps on the client-side.
This gives clear benefits over raster images:
 (i) the styling of the maps can be done by UI developers that can use CSS and scripts to style the road elements,
 (ii) vector tiles can be smaller in size as vectors are typically much smaller than a rendered bitmap, and
 (iii) it allows for all elements on the map to become interactive.
Existing implementations include the Mapbox vector tiles and Open Map Tiles.
Each have their own specificities and schemas (see [https://docs.mapbox.com/vector-tiles/mapbox-streets-v8/](https://docs.mapbox.com/vector-tiles/mapbox-streets-v8/) and [https://openmaptiles.org/schema/](https://openmaptiles.org/schema/)) with a strong focus on rendering maps.

[Valhalla by Mapzen and now hosted by the Linux Foundation](https://github.com/valhalla/valhalla) is the first project that implements the idea of vector tiles for route planners in an open-source project.
The technology proposes a [tiling specification](https://github.com/valhalla/valhalla/blob/master/docs/tiles.md) for storing routing information on disk.
Tiling the data makes sure the server can be selective about the data that needs to be loaded into memory in order to execute an individual request.
This tiling specification in Valhalla is however not used as an exchange format – although offline routing is an upcoming feature – and interoperability with other datasets is not a focus.

[Linked Geo Data](cite:cites SLHA11) is an initiative that maps Open Street Map data to Linked Data.
It releases data dumps, subject pages and a SPARQL endpoint.
Furthermore, it has their own mappings from the Open Street Map data model to a Linked Geo Data ontology.

### Open Data publishing

Open Data can be published in various interfaces.
In order to be able to query these interfaces, [Comunica](cite:cites taelman_iswc_2018) was built.
It is a Linked Data user agent that can run federated queries over several heterogeneous Web APIs, such as data dumps, SPARQL endpoints, Linked Data documents and [Triple Pattern Fragments](cite:cites tpf).
This engine has been developed to make it easy to plug in specific types of functionality as separate modules. Such modules can be added or removed depending on the configuration. As such, by looking for affordances in Web APIs, more intelligent user agents can be created.
Preconditions for an engine like Comunica to work with a dataset is: supporting a Linked Data representation and allowing cross origin resource sharing headers in the HTTP responses.
The better the data is split in fragments, the better the caching will be able to provide a faster user-perceived performance.

For public transport systems, instead of publishing a dump of time schedules or a full fletched route planner, [Linked Connections](cite:cites colpaert_2015) proposes a publishing mechanism that gives clients access to the data in time fragments.
It uses departure-arrival pairs from a station to another (a connection), and orders these connections by departure time.
It then fragments this dataset in documents that can be published over HTTP.
Links in the responses ensure a client can always find more information to take into account.
