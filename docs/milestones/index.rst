.. include:: /_static/inc_styles.txt

.. index:: milestones, speaker; start/end markup

Milestones
==========

|badge_3.0|

USFM 3.0 provides a general syntax for indicating the start and ending milestones for a span of text, where the boundaries of the content being marked may cross one or more paragraph boundaries.

A milestone type markup is required when a document has two or more structures that interact in a non-hierarchical manner. This is also referred to as *overlapping* or *concurrent* markup. A principle example of this type of overlapping structure in scripture text is the contrast between 1) the paragraph structures used to express the discourse / narrative of the text and 2) the division of the text into books, chapters and verses. In scripture texts encoded using USFM (and similarly also in `USX <https://ubsicap.github.io/usx/index.html>`_), the paragraph level markup forms the main structure of the document, while :ref:`chapter <usfmp_c>` and :ref:`verse <usfmc_v>` markers are effectively a milestone type.

Another example of an overlapping structure exists when there is a need to indicate the start and end of the quotations of the "actors" who are speaking within the text. These spans of text will commonly cross paragraph boundaries.

.. _milestones_syntax:
.. index:: milestones; syntax

General Syntax
^^^^^^^^^^^^^^

Milestones follow a syntax similar to the current :doc:`character level markup </characters/index>`. The significant distinguishing feature is that milestones introduce a new **self-closing** syntax. This self-closing syntax is the feature which identifies the marker as a milestone. The milestone will mark the *position* of the start or end of a span of text, but it does not strictly *contain* the text, as with a regular character level markup.

A benefit of the self-closing marker syntax is that it also results in a shorter marker string.

Self closing markup is indicated by immediately terminating the marker, and any attributes, with a backslash plus asterisk.

**Example:** (milestone for the start of a quotation / speaker)

.. code-block:: text

    \qt-s\*

.. _milestones_startend:
.. index:: milestones; start and end

Indicating Start and End Milestones
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

A milestone marker must always end with either ``-s`` or ``-e``

* ``-s`` indicates that the milestone is for marking the **start** of a span of text.
* ``-e`` indicates that the marker is an **end** milestone.

**Example:** (milestone for the end of a quotation / speaker)

.. code-block:: text

    \qt-e\*

.. _milestones_attributes:
.. index:: milestones; attributes

Attributes
^^^^^^^^^^

Following the syntax for :doc:`word level attributes </attributes/index>`, the following optional attributes can be added to *any* USFM milestone marker.

:id: A unique identifier which can be used to unambiguously associate the start and ending milestone marker. |br|
	The id can be composed of any mixture of numbers, letters, and underscores, and should be unique throughout the scripture text for the selected milestone type.

**Example:**

.. code-block:: text

    \qt-s |id="123" who="Pilate"\*“Are you the king of the Jews?”\qt-e |id="123"\*

Additional attributes may be available for or required by a specific USFM milestone marker (e.g the use of the ``who`` attribute in the above :ref:`quotation milestone <usfmm_qt#-s>` example).

Levels
^^^^^^

As with other USFM :ref:`numbered markers <syntax_numberedMarkers>`, a numeric variable may be added to a milestone marker to indicate a relative weighting or level. In the example of the quotation / speaker milestone, a numbered version of the marker may be used to indicate the level of nesting of the quotation being marked (i.e. a quote within a quote).

The unnumbered version may be used when only one level of marker exists within the project text. Numbers should always be included when more than one level of the marker exists within the project text.

-----

.. _usfmm_qt#-s:
.. index:: marker; \qt#-s\*, marker; \qt#-e\*, milestone; \qt#-s\*, milestone; \qt#-e\* 

\\qt#-s\\* ... \\qt#-e\\*
^^^^^^^^^^^^^^^^^^^^^^^^^

|badge_3.0|

:Syntax: ``\qt#-s\*`` ... ``\qt#-e\*``
:Type: milestone
:Added: 3.0
:Use: Quotation start / end milestones. |br|
	Typically used for indicating the speaker of the text. |br|
	The variable # represents the level of nesting of the quotation being marked (i.e. a quote within a quote). |br|
	**\\qt-s\\* = \\qt1-s\\*** |br|
	**\\qt-e\\* = \\qt1-e\\*** (see :ref:`syntax notes <syntax_numberedMarkers>` on numbered markers)

.. _usfmm_qt#-s-attr:
.. index:: attributes; \qt#-s\*, quotation milestones; attributes

.. rubric:: Attributes |ico_Tag|

Following the syntax for :doc:`word level attributes </attributes/index>`.

:who: The speaker of the quotation.

.. code-block:: text

    \qt-s |id="qt123" who="Pilate"\*“Are you the king of the Jews?”\qt-e |id="qt123"\*

**Text Samples**

Matthew 27:11-14 (GNT) - Start and end quotation milestones using ``who`` attribute; no levels.

.. code-block:: text
    :name: usfm-milestone_qt#s_example
    :emphasize-lines: 2-4,6-7

    \v 11 Jesus stood before the Roman governor, who questioned him. \qt-s |who="Pilate"\*“Are 
    you the king of the Jews?”\qt-e\* he asked.
    \p \qt-s |who="Jesus"\*“So you say,”\qt-e\* answered Jesus.
    \v 12 But he said nothing in response to the accusations of the chief priests and elders.
    \p
    \v 13 So Pilate said to him, \qt-s |who="Pilate"\*“Don't you hear all these things they 
    accuse you of?”\qt-e\*
    \p
    \v 14 But Jesus refused to answer a single word, with the result that the Governor was greatly 
    surprised.

Acts 17:22-31 - Start and end quotation milestones using ``who``, ``level``, and ``id`` attributes.

.. code-block:: text
    :name: usfm-milestone_qt#s_example-alt
    :emphasize-lines: 2-3,17,20,29
    
    \p
    \v 22 Paul stood up in front of the city council and said, \qt1-s |id="qt_ACT17:22" 
    who="Paul"\*“I see that in every way you Athenians are very religious.
    \v 23 For as I walked through your city and looked at the places where you worship,
    I found an altar on which is written, ‘To an Unknown God.’ That which you worship, then,
    even though you do not know it, is what I now proclaim to you.
    \v 24 God, who made the world and everything in it, is Lord of heaven and earth and does 
    not live in temples made by human hands.
    \v 25 Nor does he need anything that we can supply by working for him, since it is he 
    himself who gives life and breath and everything else to everyone
    \v 26 From one human being he created all races of people and made them live throughout 
    the whole earth. He himself fixed beforehand the exact times and the limits of the places 
    where they would live.
    \v 27 He did this so that they would look for him, and perhaps find him as they felt 
    around for him. Yet God is actually not far from any one of us;
    \v 28 as someone has said,
    \q1 \qt2-s |who="someone"\*‘In him we live and move and exist.’\qt2-e\*
    \b
    \m It is as some of your poets have said,
    \q1 \qt2-s |who="some poets"\*‘We too are his children.’\qt2-e\*
    \b
    \m
    \v 29 Since we are God's children, we should not suppose that his nature is anything like 
    an image of gold or silver or stone, shaped by human art and skill.
    \v 30 God has overlooked the times when people did not know him, but now he commands all of 
    them everywhere to turn away from their evil ways.
    \v 31 For he has fixed a day in which he will judge the whole world with justice by means of 
    a man he has chosen. He has given proof of this to everyone by raising that man from death!”
    \qt1-e |id="qt_ACT17:22"\*

The ``id`` in the above example has been formed using a combination of the milestone type and start milestone reference.