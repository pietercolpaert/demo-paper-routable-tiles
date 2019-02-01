## Abstract
<!-- Context      -->
Today, providers of route planning services first integrate datasets manually before offering a Web service to developers.
<!-- Need         -->
Following the open world assumption, open datasets published on the Web can provide more information for calculating the weights in user specific route planning graphs.
For example, an extra dataset of bike sharing availabilities may help the occasional cyclist.
<!-- Task         -->
In order for an ecosystem of route planners reusing open dataset to flourish, a strategy needs to be thought of to automate the adoption of these datasets in route planners.
<!-- Object       -->
Starting at the beginning, we chose to republish Open Street Map’s road network in “Routable Tiles”, similar to how vector tiles work, but in JSON-LD.
In a demo, we show how a client-side code can automatically discover the tiles download and perform a shortest path algorithm.
<!-- Findings     -->
Parallels can be seen with existing solutions, yet we see four important contributions:
(i) we launched a world-wide open dataset that is available for everyone to reuse at no cost,
(ii) we published a Linked Data version of the Open Street Map ontology,
(iii) the mapping scripts, demo and routing scripts are available as open source software, and
(iv) we introduced a hypermedia specification for vector tiles that extends the Hydra ontology.
<!-- Conclusion and Perspectives -->
The preliminary conclusions of this work put forward more questions than answers:
are existing RDF serializations compact enough?
What happens when another dataset needs to introduce new nodes that are not in the base map?
Can other hypermedia structures be thought of?


