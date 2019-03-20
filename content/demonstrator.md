## Demonstrator
{:#demonstrator}

The server has been set-up for the entire world at [https://tiles.openplanner.team/planet/14/{x}/{y}/](https://tiles.openplanner.team/planet/14/8411/5485/). A live demonstrator using this data can be found at [https://openplannerteam.github.io/leaflet-routable-tiles/](https://openplannerteam.github.io/leaflet-routable-tiles/).

<figure id="listing2">
<div class="printonly">
<!--<img src="img/routabletiles.png" class="printonly"/>-->
See the <a href="http://pieter.pm/demo-paper-routable-tiles/#demonstrator">online paper</a> which includes the demo, or visit <a href="https://openplannerteam.github.io/leaflet-routable-tiles/">https://openplannerteam.github.io/leaflet-routable-tiles/</a>
</div>
<iframe class="noprint" src="https://openplannerteam.github.io/leaflet-routable-tiles/#latitude=45.515570&longitude=13.595109" style="width: 100%; height: 50vh;">
</iframe>
<figcaption>A demonstrator of what you can do with Routable Tiles. You can pan around, select another city, and calculate a shortest path. Both rendering the map and the route planning happens on the client-side while loading the tiles dynamically.</figcaption>
</figure>

The data is used for rendering the map as well as routing.
As every tile contains global identifiers for each Way, Node and Relation, these identifiers can be reused by third parties.
Furthermore, the properties that are added on top of these resources can share properties, and automated alignment through reasoning can enrich the existing data.
We discuss the open challenges in the last chapter.
