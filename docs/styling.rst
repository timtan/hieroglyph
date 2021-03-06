.. _hieroglyph-themes:

================
 Styling Slides
================

Styling
-------

- Slides are contained in ``<article>`` elements
- Each slide has an HTML ``id`` that corresponds to the permalink ID
  generated by Sphinx (for example, you're currentling reading
  ``styling``).
- The heading level is added as a class; ie, ``level-2``
- Slides may be styled using a theme, or custom CSS.

Included Themes
---------------

Hieroglyph includes two :ref:`themes <custom-themes>`.

``slides``

  Two slides levels: the first level of headers become "section"
  headers, and the second become the real content.

``single-level``

  Only one style of slide, every slide has a title at the top.


Setting the Theme
-----------------

You can set your theme using the ``slide_theme`` configuration
setting.

::

  slide_theme = 'single-level'

If you're using a custom theme, you can also set the directory to look
in for themes::

  slide_theme_path = '...'

.. _custom-css:

Custom CSS
----------

The standard Hieroglyph themes support adding a custom stylesheet with
the ``slide_theme_options`` dict in ``conf.py``::

  slide_theme_options = {'custom_css':'custom.css'}

The custom CSS file should be located in the ``html_static_path``
(``_static`` by default).

.. _custom-themes:

Creating  Themes
----------------

Hieroglyph themes are based on Sphinx's HTML `themes`_. Themes are
either a directory or zipfile, which contains a ``theme.conf`` file,
templates you wish to override, and a ``static/`` directory which
contains images, CSS, etc.

When defining a slide theme, inherit from the ``slides`` theme for
basic support. For example, the ``single-level`` them has the
following ``theme.conf``::

  [theme]
  inherit = slides
  stylesheet = single.css

  [options]
  custom_css =

In order to include the base slide styling, your theme's stylesheet
should begin with::

  @import url(slides.css);

``slides.css`` will be supplied by the base theme (``slides``).

See the Sphinx documentation for `themes`_ for more information.

.. _`themes`: http://sphinx.pocoo.org/theming.html
