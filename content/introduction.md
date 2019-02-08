<div class="printonly">This is a print-version of a paper first written for the Web. The Web-version is available at http://pieter.pm/locweb2019-theweb-routable-tiles/</div>

## Introduction
{:#introduction}

When setting up a Web-based journey planner that takes into account individual user needs, 
developers are confronted with the daunting prospect of integrating heterogeneous datasets. 
Industry players provide an alternative solution to this tangle, 
by providing services on top of their datasets that are centralized in one location. 
They are able to provide a solution for the Pareto principle's 80% 
and build a business around that. 
When trying to cater to the remaining 20%, 
industrial route planners are quickly confronted 
with diminishing returns of integrating more datasets.

Take for example use cases of people owning a foldable bike 
that can take their bike on public transport, 
companies trying to find an optimal delivery route for their delivery service 
where some vehicles cannot pass through low emission zones, 
routes based on the real-time state of traffic control systems 
and probability to hit a green light 
or people with special constraints or disabilities.

For each of these use cases, 
extra datasets are needed to calculate these end-user specific routing graphs. 
Such datasets are published by different organizations 
that often publish them openly, thanks to strategic goals or legal mandates. 
Every route planner will somehow need to compile their own sources 
over which they can execute their own route planning algorithm.

In this paper, we aim to automate data adoption in route planners 
and as a first step we decided to introduce “Routable Tiles”. 
Routable Tiles is a specification in which we republished all the roads in Open Street Map 
using a tiling mechanism that exploits Open Data principles. 
In the next section we will see that the ideas behind Routable Tiles itself is not novel, 
yet to the best of our knwoledge, 
publishing routable tiles for clients to consume has not been done before. 

After introducing the ontology, specification and server software, 
we demonstrate what now becomes possible in an in-browser demo. 
The browser itself can perform a routing algorithm on the client-side, 
and every step in the routing algorithm can involve other weights and datasets as it pleases. 
This first prototype exploiting Open Data principles probably introduces more questions than answers 
as we discuss in the conclusion and discussion section.