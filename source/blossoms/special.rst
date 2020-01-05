``print``
---------

Print one or more data-items as a table.

**Example**:

::

    - packages = [ "nano", "vim" ]
    - test_output = "test"
    - test_file = "/proc/cpuinfo"

    print("test-output")
    - packages = packages
    - some_output = test_output
    - command = "cat {{test_file}}"


Output:

::

    +-------------+-------------------+
    | Item-Name   | Value             |
    +=============+===================+
    | command     | cat /proc/cpuinfo |
    +-------------+-------------------+
    | packages    | ["nano","vim"]    |
    +-------------+-------------------+
    | some_output | test              |
    +-------------+-------------------+


**Input**:

.. tabularcolumns:: |m{0.4\textwidth}|m{0.15\textwidth}|m{0.38\textwidth}|

.. list-table::
    :header-rows: 1

    * - **Name**
      - **Type**
      - **Description**

    * - (any name, which should be shown in the output)
      - any data type
      - Item which should be printed on the terminal. Even array- and map-items can be printed.

**Output**:

    no output



``assert``
----------

Assert for one or more data-items to have a specific content.

**Example**:

::

    - test_item = "test"
    - another_item = ["test"]

    assert("test-assert")
    - test_item == "test"
    - test_item == another_item.get(0)


**Input**:

* left side: name of the item, which should be checked

* right side: value or data-item to compare with
     

**Output**:

    no output

**Restrictions**

    * On the left side, only a single item name is allowed. Calling a function on the left side would result in a parser error.

    * At the moment only "==" is supported.



``cmd``
-------

Run a custom shell command.

**Example**:

::

    - test_file = "/proc/cpuinfo"

    cmd("test-command")
    - command = "cat {{test_file}}"


**Input**:

.. tabularcolumns:: |m{0.15\textwidth}|m{0.15\textwidth}|m{0.63\textwidth}|

.. list-table::
    :header-rows: 1

    * - **Name**
      - **Type**
      - **Description**

    * - command
      - string-value
      - Command, which should be executed
     

**Output**:

    - string-value with the stdout content of the called tool

**Restrictions**

    * stderr content of the called tool is discarded

    

``exit``
--------

Kill the current run and close the tool with a specific exit code.

**Example**:

::

    exit("kill run")
    - status = 42

**Input**:

.. tabularcolumns:: |m{0.15\textwidth}|m{0.15\textwidth}|m{0.63\textwidth}|

.. list-table::
    :header-rows: 1

    * - **Name**
      - **Type**
      - **Description**

    * - status
      - int-value
      - exit status code of the tool
     

**Output**:

    no output

.. raw:: latex

    \newpage
