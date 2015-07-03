# Introduction #

The original relations ontology (ID space "OBO\_REL") was a direct translation of the 2005 RO paper into OBO format. It suffered a number of problems, such as lack of clarity in the semantics of class level relations.

Here we use "RO" to refer to the obo/owl version of the current ontology, and "OBO\_REL" to refer to the original 2005 version.

Note that many of the differences described here [were originally announced on the RO and BFO lists](http://groups.google.com/group/obo-relations/browse_thread/thread/29fc616eb570f7dc/fc0647f190b5f178)

# Differences #

## Identifiers / IRIs ##

OBO\_REL used identifiers of the form "OBO\_REL:part\_of", which were translated to URIs of the form http://obofoundry.org/ro#part_of

RO follows the obofoundry ID policy and uses numeric identifiers with corresponding IRIs of the form http://purl.obolibrary.org/obo/RO_nnnnnnn

See [Identifiers](Identifiers.md) for more details

## Ceding of relations to BFO ##

We have ceded some core relations to BFO, where they are generic and are required to define BFO classes.

Examples:

**http://purl.obolibrary.org/obo/BFO_0000050 is part of (replaces OBO\_REL:part\_of)**

These relations are part of the proposed BFO1.2. ontology

_UPDATE_: See [ROAndBFO](ROAndBFO.md) for latest here

## Elimination of class-level relationships ##

The original OBO\_REL followed the Genome Biology paper in defining relations as class-level. However, these class-level relations caused a lot of confusion and are not really required - in OWL (and in OBO-Format, which is a subset of OWL) we have instance level relationships that are quantified (e.g. finger SubClassOf part\_of **some** hand).

RO makes a clean break with OBO\_REL, and abandons class level relations.

For a discussion of how RO aligns with OBO\_REL in terms of temporal quantification, see [ROAndTime](ROAndTime.md).

An exception is made for a small number of "macro" relations such as [RO\_0002161](http://purl.obolibrary.org/obo/RO_0002161) (never in taxon), which is modeled as an annotation property and expanded to a more complex OWL statement using an OWL macro expansion engine. See the OWL macros section of the obo format spec for more details

## Source format ##

For OBO\_REL, the source was obo-format, and OWL was derived from this. There was an experiment to use Common Logic Interchange Format as the source, but this was abandoned.

The source version of RO is in OWL, and a subset of this is translated to generate ro.obo

## Elimination of builtins ##

OBO\_REL followed the Genome Biology paper in declaring relations "instance\_of" and "is\_a". These have been eliminated in RO, because they are redundant with existing OWL predicates (class assertion and subclass, respectively).

Note that the differences between these relations as defined in the Genome Biology paper and the OWL predicates is a difficult and partly controversial issue. For the purposes of RO and the majority of RO users, the OWL predicates suffice, and there is no use case for additional relations