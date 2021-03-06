tablepy usage
=============

the python tablepy package can be used to easily create and render tables.
As of right now it only supports rendering lists of lists in tabular form. 

|

it defines the following:

* :py:func:`tablepy.printTable`

* :py:func:`tablepy.clearSlait`

* :py:func:`tablepy.destroyAll`

* :py:class:`htmlTable`


.. note::

   for demonstrational perpaces I will use the input list:

   .. code-block:: python

      m =[["", "hello", "good by"],
          ["fr", "salut", "aurevoir", "bon jour"],
          ["de", "hallo"]]


.. py:function:: tablepy.printTable(table, renderInner=Fasle, filler="")
   
    render a 2d matrix in tabular form. any missing elements will be replaced with the parameter ``filler``. the renderInner parameter will render all the lines inside the table if True. 
    ``tablepy.printTable(m)``
    will output:

   .. code-block:: python

           +-------------------------------------+
           |          hello    good by           |
           | fr       salut    aurevoir bon jour |
           | de       hallo                      |
           +-------------------------------------+
     and with renderInner True
          +----------+----------+----------+----------+
          |          | hello    | good by  |          | 
          +----------+----------+----------+----------+
          | fr       | salut    | aurevoir | bon jour | 
          +----------+----------+----------+----------+
          | de       | hallo    |          |          | 
          +----------+----------+----------+----------+

.. py:function:: tablepy.clearSlait()

    remove all cash data created by :py:class:`htmlTable`. 
    
    .. warning::
        this function will affects every interpreter instance ans should be used sparingly. it basicly deletes everything. to only destroy this interpreters cash use :py:func:`tablepy.destroyAll`

.. py:function:: tablepy.destroyAll()

   remove all cash data created by :py:class:`htmlTable` in this instance of the interpreter. to remove all cash data use :py:func:`tablepy.clearSlait`.

|

.. py:class:: htmlTable(inp, ...)

    | the htmlTable class can be used to create html documents containing tables and open them in a         browser. 

    :param list[list[object]] inp: the input table from witch to generate the table from. The genration works identicly to the one used by :py:func:`tables.printTable`.
    :param str name: the title of the table it doesn't have any further meaning, default is ``table``
    :param int keyRowIdx: what row to write in bold letters, if -1 or not a valid value it will not show anything in bowld, default is -1.
    :param int keyColIdx: same as keyRowIdx but for the collums
    :param int border: how thick the border of the table should be.
    :param str encoding: what the encoding system should be defaults to ``utf-8``
    :param str caption: the catpion of the table, defaults to ``""``

    .. py:method:: cash()

        resaves the table to the libraries html cash witch can be cleared using :py:func:`tablepy.clearSlait()` or :py:func:`tablepy.destroyAll()`

    .. py:method:: open():

        open the generated html file using :ref:`webbrowsers <https://docs.python.org/3/library/webbrowser.html>` open function.


    .. py:method:: open_new():

        open the generated html file using :ref:`webbrowsers <https://docs.python.org/3/library/webbrowser.html>` open_new function.

    .. py:method:: open_new_tab():

        open the generated html file using :ref:`webbrowsers <https://docs.python.org/3/library/webbrowser.html>` open_new_tab function.

    .. py:method:: delete():
        
        delets all cashed data generated by this html table.

    .. py:method:: copyFile(path):

        copies the cashed html file to path
        :param str path: a valid os path to copy the html file to

:doc:`index`
