Introduction
============

This product will add to Plone a new content rules, someway similar to the default "*Send an email*" ones.
The difference is that the email recipient is taken dinamically from the content itself, not from a
defined list of values.

In this way the same rule, applied in different places of the site, can warn different users.

How to use
==========

The rules can be enabled globally and locally like every one else, as default Plone feature.

In the rule configuration panel you need to fill a set of information:

 ``Subject``
     The e-mail subject. You can place inside this text some markers (see below).
 ``Sender email``
     XXX

TODO
====

* why don't support also looking in annotations?
* why don't support also multiple valued sources?
* right now the rules check all mail source until one is found with a defined order;
  maybe is better to leave this choice to users 
