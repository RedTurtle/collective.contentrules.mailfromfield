.. contents::

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
    The sender of the e-mail. You can leave this empty and automatically use the one from the
    site mail settings.
``Source field``
    You must put there the name of the attribute from which you want to retrieve the recipient
    e-mail. See next section.
``Target element``
    You need to select there if the recipient's e-mail must be taken from the object where the
    rule is activated on ("*From trigger object*", default choice) or from the document that
    really raised the event ("*From event target*").
    
    See next section.
``Mail message``
    The body text of the e-mail that will be sent. The text is the same for all section where
    the rule is activated on.
    
    You can place inside this text some markers (see below).

How the address is taken (and from which object)
------------------------------------------------

First of all you must choose the type of *target element*.

If you choose to keep default "*From trigger object*", the data is read from the section you have
activated the rule on.
Example: if you activate the rule on a folder called ``section`` and a rule activated in this section
will raise event when working on a document called ``foo`` (like: modifying the document), the e-mail
address will be taken from the folder

Changing to "*From event target*" will change the behaviour, trying to get e-mail data from
the same attribute but looking for it on the object that raised the event.
In the example above we will look for the value from the document.

What we'll try to read
----------------------

The rule try to get from the object:

* an attribute of the given name
* a callable method from the given name
* an Archetypes field with given id
* a ZMI property with given id

The rule try to read, one after one, all this data. The first match found will be the one used;
if not one give results, no e-mail is sent at all.

Message markers
---------------

Marker labels that follow can be used in the message text and subject.

``${title}``
    The title of the content that triggered the event (``foo`` title in our example)
``${url}``
    The URL of the content that triggered the event (``foo`` URL in our example)
``${section_name}``
    The title of the folder where the rule is activated on (``section`` title in our example)
``${section_url}``
    The URL of the folder where the rule is activated on (``section`` URL in our example)

TODO
====

* why don't support also looking in annotations?
* why don't support also multiple valued sources?
* right now the rules check all mail source until one is found with a defined order;
  maybe is better to leave this choice to the configuration

Requirements
============

This product has been tested on:

* Plone 3.3
* Plone 4.1

Credits
=======

Developed with the support of `S. Anna Hospital, Ferrara`__; S. Anna Hospital supports the
`PloneGov initiative`__.

__ http://www.ospfe.it/
__ http://www.plonegov.it/

Authors
=======

This product was developed by RedTurtle Technology team.

.. image:: http://www.redturtle.it/redturtle_banner.png
   :alt: RedTurtle Technology Site
   :target: http://www.redturtle.it/

