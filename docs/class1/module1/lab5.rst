Lab 1.5: Building Imperative Workflows with Postman Collections
---------------------------------------------------------------

.. graphviz::

   digraph breadcrumb {
      rankdir="LR"
      ranksep=.4
      node [fontsize=10,style="rounded,filled",shape=box,color=gray72,margin="0.05,0.05",height=0.1]
      fontsize = 10
      labeljust="l"
      subgraph cluster_provider {
         style = "rounded,filled"
         color = lightgrey
         height = .75
         label = "BIG-IP"
         basics [label="REST Basics",color="palegreen"]
         authentication [label="Authentication",color="palegreen"]
         globalsettings [label="Global Settings",color="palegreen"]
         networking [label="Networking",color="palegreen"]
         clustering [label="Clustering"]
         transactions [label="Transactions"]
         basics -> authentication -> globalsettings -> networking -> clustering -> transactions
      }
   }

As you have seen in the previous labs, we can use the Collections and Folders
features of the Postman client to group REST requests logically.  Additionally,
as you've seen most of the examples so far have consisted of executing a
sequence of REST request to achieve some outcome.

In this lab, we will use a feature in Postman called the **Collection Runner
(Runner)** to execute a sequence of REST requests.  Using the Runner we can
rapidly prototype REST requests into an **Imperative Workflow** that can be
executed without user intervention.

The purpose of this exercise is to provide an example of how new workflows can
be built from scratch or existing workflows can be modified.

Additionally, we will use some Postman Javascript Tests to programmatically
populate environment variables with the output of our workflow.

Task 1 - Open and Run a Collection
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#. The collection we will run in this task will populate some environment
   variables with various data about the BIG-IP system.  First, let's examine
   the Environment Variables that are currently set.  Click the |lab-5-2|\ icon
   in the top right of the Postman window.  Notice that there are no variables
   starting with the name ``lab1.5_``:

   |lab-5-1|

#. Click the ``Lab 1.5 - Building Imperative Workflows`` folder to expand it

#. Click the ``Step 1: Get BIG-IP Software Version`` request.  Click the
   :guilabel:`Tests` tab and examine the Javascript code and comments:

   |lab-5-3|

   The Javascript code in the Test script will populate an environment variable
   based on the response from the BIG-IP system.

#. Click the :guilabel:`Runner` button at the top left of your Postman window:

   |postman-runner-button|

#. Select the ``F5 Programmability: Class 1`` Collection then the
   ``Lab 1.5 - Building Imperative Workflows`` folder.  Next, be sure the
   environment is set to ``F5 Programmability: Class 1`` and ``Persist Variables``
   is selected:

   |lab-5-4|

   Your Runner window should look like:

   |lab-5-5|

   As you can see from the screenshot or your own Collection Runner screen, we
   will be sending 3 requests (Steps 1-3 in Lab 1.5).  Each request has a
   *unit test* implemented in JavaScript to ensure it's ok to continue to the
   next request when using the Collection Runner. The Runner will step through
   each request unless one of the tests fails.

#. Click the :guilabel:`Run Lab 1.5 - Buil...` button

#. The results window will now populate.  You will see each request in the
   folder is sent and its associated test results are displayed on the screen.
   The last request in the folder includes some Javascript code to dump the
   results to the screen:

   |lab-5-6|

#. Next, switch back to the main Postman window.  Click the |lab-5-2|\ button
   again and examine the environment variables.  Notice that three new variables
   starting with the name ``lab1.5_`` have been populated. You may need to scroll
   down to see these variables:

   |lab-5-7|

.. NOTE:: It is normal for the values of Software Version, CPU Count and Base
   MAC Address to be different from the screenshot(s).

In this lab, we demonstrated running a simple Imperative Workflow using the
Postman Collection Runner.  In subsequent labs, we will expand on this simple
use case to perform more complex functions.  As you continue through the labs,
be sure to take time to explore the details of the requests being sent.  The
Postman Collection used in this class can also serve as a starting point for
building your own collections or modifying existing ones.

As we move through the rest of this module you will see the complexity involved
in building Imperative Workflows.  While these types of workflows are incredibly
powerful, they are also time-consuming to build from scratch.  As we move into
Module 2 you will see the importance of leveraging **Abstraction**
and **Declarative Interfaces** to minimize the amount of time spent on building
Imperative Workflows.

.. raw:: html

   <iframe width="600" height="315" src="https://www.youtube.com/embed/WxAirVNyo6I" frameborder="0" gesture="media" allowfullscreen></iframe>

*Source: https://youtu.be/WxAirVNyo6I*


.. |postman-runner-button| image:: /images/postman-runner-button.png
.. |lab-5-1| image:: images/lab-5-1.png
.. |lab-5-2| image:: images/lab-5-2.png
.. |lab-5-3| image:: images/lab-5-3.png
.. |lab-5-4| image:: images/lab-5-4.png
.. |lab-5-5| image:: images/lab-5-5.png
.. |lab-5-6| image:: images/lab-5-6.png
   :scale: 65%
.. |lab-5-7| image:: images/lab-5-7.png
