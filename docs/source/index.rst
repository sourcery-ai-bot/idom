IDOM |release|
==============

.. image:: branding/idom-logo.png
    :height: 250px

Libraries for defining and controlling interactive webpages with Python
3.6 and above.

.. toctree::
    :maxdepth: 1

    installation
    getting-started
    javascript-modules
    core-concepts
    how-it-works
    specifications
    extra-features
    examples
    glossary
    known-issues
    api


Try it Now!
-----------

- In a Jupyter Notebook - |launch-binder|

- With an online editor - `IDOM Sandbox`_


Early Days
----------

IDOM is still young. If you have ideas or find a bug, be sure to post an
`issue`_ or create a `pull request`_. Thanks in advance!


At a Glance
-----------

Let's use IDOM to create a simple slideshow which changes whenever a
user clicks an image:

.. code-block::

    import idom

    @idom.element
    async def Slideshow(self, index=0):
        async def next_image(event):
            self.update(index + 1)

        return idom.html.img(
            {
                "src": f"https://picsum.photos/800/300?image={index}",
                "style": {"cursor": "pointer"},
                "onClick": next_image,
            }
        )

    host, port = "localhost", 8765
    server = idom.server.sanic.PerClientStateServer(Slideshow)
    server.run(host, port)

Running this will serve our slideshow to ``"https://localhost:8765"``. You can try out
a working example by enabling the widget below - clicking the image should cause it to
change 🖱️

.. interactive-widget:: slideshow

.. note::

    You can display the same thing in a Jupyter Notebook using widgets!

    .. code-block::

        idom.JupyterDisplay(f"https://{host}:{port}")

    For info on working with IDOM in Jupyter see some :ref:`examples <Display Function>`.


.. Links
.. =====

.. _issue: https://github.com/rmorshea/idom/issues
.. _pull request: https://github.com/rmorshea/idom/pulls
.. _IDOM Sandbox: https://idom-sandbox.herokuapp.com
.. |launch-binder| image:: https://mybinder.org/badge_logo.svg
   :target: https://mybinder.org/v2/gh/rmorshea/idom/master?filepath=examples%2Fintroduction.ipynb
