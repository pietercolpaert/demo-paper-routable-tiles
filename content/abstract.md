## Abstract
<!-- Context      -->
Today, route planning providers manually integrate different geo-spatial datasets 
before offering a Web service to developers, thus creating a closed world view. 
In contrast, combining open datasets at runtime 
can provide more information for user-specific route planning needs. 
For example, an extra dataset of bike sharing availabilities 
may provide more relevant information to the occasional cyclist.
<!-- Need         -->
A strategy for automating the adoption of open geo-spatial datasets is needed 
to allow an ecosystem of route planners able to answer more specific and complex queries. 
This rises new challenges such us 
(i) how open geo-spatial datasets should be published on the Web to raise interoperability, 
and (ii) how route planners can discover and integrate relevant data for a certain query on the fly.
<!-- Task         --> 
We republished Open Street Map’s road network as “Routable Tiles”
to facilitate its integration into open route planners.
To achieve this, we use a Linked Data strategy and follow an approach similar to vector tiles.
<!-- Object       -->
In a demo, we show how client-side code can automatically discover tiles and perform a shortest path algorithm.
<!-- Findings     -->
We provide four contributions: (i) we launched an open geo-spatial dataset that is available for everyone to reuse at no cost, (ii) we published a Linked Data version of the Open Street Map ontology, (iii) we introduced a hypermedia specification for vector tiles that extends the Hydra ontology, and (iv) we released the mapping scripts, demo and routing scripts as open source software.
<!-- Conclusion and Perspectives -->
<!-- The preliminary conclusions of this work put forward more questions than answers: 
are existing RDF serializations compact enough for an acceptable user experience? 
What happens when another dataset needs to introduce new nodes that are not in the base map? 
Can other hypermedia structures be thought of?-->
