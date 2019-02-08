## Abstract
<!-- Context      -->
Today, route planning providers manually integrate different geo-spatial and temporal datasets before offering a Web service to developers, thus creating a closed world view. In contrast, open datasets on the Web follow the open world assumption and combining them at runtime can provide more information for user-specific route planning needs. For example, an extra dataset of bike sharing availabilities may provide more relevant information to the occasional cyclist.
<!-- Need         -->
In order for an ecosystem of route planners reusing open datasets to flourish, a strategy for automating the adoption of these datasets in route planners is needed. This rises new challenges such us (i) how open datasets should be published on the Web to raise interoperability, and (ii) how can route planners discover and integrate relevant data for a certain query on the fly.
<!-- Task         -->
To facilitate its integration into open route planners, we republished Open Street Map’s road network as “Routable Tiles” in a similar to how vector tiles work, but as Linked Data.
<!-- Object       -->
In a demo, we show how client-side code can automatically discover tiles and perform a shortest path algorithm.
<!-- Findings     -->
We provide four contributions: (i) we launched an open dataset that is available for everyone to reuse at no cost, (ii) we published a Linked Data version of the Open Street Map ontology, (iii) the mapping scripts, demo and routing scripts are available as open source software, and (iv) we introduced a hypermedia specification for vector tiles that extends the Hydra ontology.
<!-- Conclusion and Perspectives -->
The preliminary conclusions of this work put forward more questions than answers: are existing RDF serializations compact enough? What happens when another dataset needs to introduce new nodes that are not in the base map? Can other hypermedia structures be thought of?