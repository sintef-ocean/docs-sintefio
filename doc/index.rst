
.. |br| raw:: html

  <br />

Last changed: |today| |br|
**SINTEF organization website**: `https://www.sintef.no <https://www.sintef.no>`_. |br|
**SINTEF Ocean official website**: `https://www.sintef.no/ocean <https://www.sintef.no/ocean>`_.

SINTEF Ocean
------------

This site contains links to a few software projects and repositories maintained by
SINTEF Ocean.

Software
~~~~~~~~

`FhSim <https://fhsim.no/>`_
    FhSim is a software platform and framework for mathematical modelling and
    numerical simulation, with a focus on marine applications.

`RatatoskIDL <https://sintef-ocean.github.io/ratatoskidl>`_
    Project with Interface Definition Language (IDL) files as import
    targets. It provides source files so that communication APIs between applications using data
    distribution service standard `OMG DDS <https://www.omg.org/spec/DDS/About-DDS/>`_ can be generated. The IDL files are used by ``ratatosk``
    and other softwares in our portfolio.

`Sinspekto <https://sintef-ocean.github.io/sinspekto>`_
    *Sinspekto* is a module that provides Qt modeling language (`QML <https://doc.qt.io/qt-5/qtqml-index.html>`_)
    components for interacting with applications that use the data distribution service
    standard `OMG DDS <https://www.omg.org/spec/DDS/About-DDS/>`_ as communication middleware. Sinspekto consists of classes that
    define various `QML Object Attributes <https://doc.qt.io/qt-5/qtqml-syntax-objectattributes.html>`_, which are translated to / from DDS topics. This
    means that by using sinspekto QML elements in your application, it is possible to
    interact with other systems using DDS.

`conan recipes <https://sintef-ocean.github.io/status-conan-recipes/>`_
    We make use of conan to build many of our projects. This site
    contains an overview of the continuous integration build status of public recipes
    maintained by us.

R&D projects
~~~~~~~~~~~~

Add short description of fangstkontroll and links to project pages, results and more.
Point to softwares.

FHF: Catch control in Purse Seine
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. image:: ./static/fkin.png
    :align: left
    :width: 180

"Fangstkontroll i notfiske etter pelagiske arter: Fase 2" is a project funded by FHF –
Norwegian Seafood Research Fund, Grant No. 901350. See the FHF's `project page <https://www.fhf.no/prosjekter/prosjektbasen/901350/>`_ for
updated news.

As part of this project, several software programs and libraries have been
developed. In addition to improvements to ``RatatoskIDL`` and ``Sinspekto`` mentioned
above, we have developed two programs, namely ``Balder`` and ``Mimir``.

`Balder <https://sintef-ocean.github.io/balder>`_
    *Balder* is a graphical user application that provides decision support for
    the captain in purse seining before gear deployment. Balder makes use of real-time
    data and model predictive control algorithms to predict a deployment trajectory for
    the purse seine. The deployment trajectory is devised by taking into account expected
    sink depth/speed of the gear and use a prescribed trajectory of the fish school

`Mimir <https://sintef-ocean.github.io/mimir>`_
    *Mimir* serves as a simple reference implementation to achieve an
    optimization-based decision support for deployment planning. The program typically
    runs to provide algorithm outputs to another application, for instance a graphical
    application that visualizes the results. The algorithms are specifically set up to
    use the `CasADi <https://web.casadi.org>`_ framework and its interfaces to various algorithm libraries, including
    optimization problem solvers and numerical integrators.
