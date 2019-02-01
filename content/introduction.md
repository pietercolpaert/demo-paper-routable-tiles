<div class="printonly">This is a print-version of a paper first written for the Web. The Web-version is available at http://pieter.pm/locweb2019-theweb-routable-tiles/</div>

## Introduction
{:#introduction}

When setting up a new journey planner on the Web taking into account individual user needs, developers are quickly confronted with the daunting aspects of integrating heterogeneous datasets.
Industry players provide solutions to this mess, by providing services on top of their datasets that are centralized in one location.
They are able to provide a solution for 80% (based on the Pareto principle) and build a business around that.
Industry route planners are not going to find a solid business model to keep integrating datasets that may benefit any individual user of the remaining 20%.

Take for example use cases where people want to calculate trips for:
people owning a foldable bike that can take their bike on public transport,
companies trying to find an optimal delivery route for their delivery service where some vehicles cannot pass through low emission zones,
routes based on the probability and real-time state of traffic control systems to hit a red light,
people with special constraints based on a disability.

For each of these use cases, extra datasets are needed to calculate these end-user specific routing graph.
These datasets are published by different organizations that often publish their data openly thanks to legal constraints or strategic goals.
Every route planner will somehow need to compile their own sources which they want to take into account.

In this paper, we aim to automate data adoption in route planners, and as a first step decided to introduce “Routable Tiles”.
Routable Tiles is a specification in which we republished all the roads in Open Street Map using a tiling mechanism that exploits Open Data principles.
In the next chapter we will see that the ideas behind Routable Tiles is not that novel, yet somehow publishing routable tiles for clients to consume has not been done before.
After introducing the ontology, specification and server software, we demonstrate what now becomes possible in an in-browser demo.
The browser itself can perform a routing algorithm on the client-side, and every step in the routing algorithm can involve other weights and datasets as it pleases.
This first prototype exploiting Open Data principles probably introduces more questions than answers.
