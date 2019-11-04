NL-Explanations
===============



The article
===========

Link for the publication_.

.. _publication: http://www.madgik.di.uoa.gr/sites/default/files/icde10_pp333-344.pdf

Problem to address
^^^^^^^^^^^^^^^^^^

The problem that this article tries to tackle down is the translation of a query created with a structured query language, into natural language.

This feature comes handy in a couple of circumstances:

First, when using a form-based interface connected with a database which produces implicitly structured queries, such tool could help the user -that may be not familiar with the structure of the database- by presenting in a more familiar way the result of the user's selections.

Query translation can also be useful as an intermediate step between editing a query and its execution.
An accurate translation of this query can prevent the user from unexpected results or even errors.

The difficulty
^^^^^^^^^^^^^^

The difficulties that occur, do vary:

- Insufficient SQL semantics,

- The complexity of queries, like:

	- nested queries,
	- complex query conditions,
	- different query constructs (group-by, order-by, etc.),

- and last but not least, the naturalness of the produced statement

The last part is crucial. There are many different ways to present a query in natural language. This makes the selection of the order in which the algorithm

Solution
^^^^^^^^

The article takes a graph-based approach.

**The Schema**

In the beginning of the executions, it fetches the schema of the database and creates a directed graph, the SchemaGraph. As nodes in this graph we have the relations(tables) and their attributes(columns). 

As edges we have the membership edges that connect an attribute node to its relation node (e.g. client_id `of` client), selection edges that connect a relation node to its attribute nodes (e.g. client `whose` client_id) and predicate edges that start from an attribute node and end to another attribute node of another relation. The predicate nodes represent a potential join between two relations.

**The Query**

After that, 

The code
========

Database Preperation
^^^^^^^^^^^^^^^^^^^^

**Database Schema**

	- scrap all tables except the ones that start with 'translation'

**Translation Tables**

``translation_attribute_node_labels`` *table, column, label* (e.g.: 'addresses', 'address_id', 'ID')

``translation_primary_relations``  *table*

``translation_relation_node_labels`` *table, label*

``translation_heading_attributes`` *table, column*

``translation_edge_operators`` *id, operator* (e.g.: 1, '<')

``translation_edge_types`` *id, type_names* (e.g.: 1, 'MEMBERSHIP')

``translation_paths`` *id, template_id, link_point, where, having, group*

``translation_specific_templates`` *id, labels* (e.g.: 1, 'l(clients)+" who live in "+addresses.town_city.<val>')

``translation_edges`` *id, path_id, from, to, type, operator* (e.g.: 14, 1, 'clients', 'client_id', 4, 7)


Structure
^^^^^^^^^

Run it
^^^^^^


Impovements - Ideas
===================

.. toctree::
   :maxdepth: 2
   :caption: Contents:



Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`
