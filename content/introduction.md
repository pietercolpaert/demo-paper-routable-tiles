<div class="printonly">Read the HTML-version: <a href="https://pieter.pm/demo-paper-routable-tiles/">http://pieter.pm/demo-paper-routable-tiles/</a></div>

## Introduction
{:#introduction}

When setting up a Web-based journey planner that takes into account individual user needs, 
developers are confronted with the daunting prospect of integrating heterogeneous datasets. 
Industry players provide an alternative solution to these complexities, 
by providing services on top of their datasets that are centralized in one location. 
They are able to provide a solution for the ~80% of the world-wide needs 
and build a business around that. 
When trying to cater to the remaining 20%, 
industrial route planners are quickly confronted 
with diminishing returns of integrating more datasets.
Take for example use cases of (i) people owning a foldable bike and the ability to take their bike on public transport, 
(ii) companies trying to find an optimal delivery route for their delivery service where some vehicles cannot pass through low emission zones, 
(iii) routes based on the real-time state of traffic control systems and probability to hit a green light,
or (iv) people with special constraints or disabilities.
For each of these four use cases, 
extra datasets are needed to calculate these end-user specific routing graphs. 
Such datasets are published by different organizations
that often publish them openly, thanks to strategic goals or legal mandates. 
Every route planner will somehow need to compile their own sources 
over which they can execute their own route planning algorithm.

In this paper, we aim to automate data adoption in route planners.
As a first step, we introduce *Routable Tiles*. 
This is a hypermedia specification for geospatial road networks.
In this specification, we republished all the roads in Open Street Map.
In the next section we will see that the ideas behind Routable Tiles itself is not novel.
The contribution of this paper lies in applying the geospatial indexing idea from the database world
to Web APIs, introducing an ontology for describing geospatial hypermedia controls,
and launching this world-wide dataset as a resource to the Semantic Web community.

<!--After introducing the ontology, specification and server software, 
we demonstrate what now becomes possible in an in-browser demo. 
The browser itself can perform a routing algorithm, 
and every step in the routing algorithm can thus involve other weights and datasets as it pleases.
Finally, we discuss the open challenges that arose publishing the data for client-side adoption in the conclusion and discussion section.-->
