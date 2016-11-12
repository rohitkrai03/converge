SETTINGS MANAGEMENT
===================

-  Settings files are usual Python files that can contain valid python
   code however here are some guidelines for user
-  use module variables for global application wide configuration
-  Use UPPERCASE while naming settings variables
-  For values prefer basic python datatypes usch as string, integer,
   tuples
-  eg. ``SERVER_PORT = 1234``
-  Avoid logic
-  Use simple classes for config sections

   -  eg.

      ::

          class DB:
              HOST = 'db.example.com'
              PORT = 1234

-  Use simple string operations to avoid repeatation
-  eg::

    BASE_DOMAIN = 'example.com'
    API_URL = 'api.' + BASE_DOMAIN``

Supported settings files
-------------------------

-  Defaults: default_settings.py
-  Mode
    - Production: prod_settings.py
    - Development: dev_settings.py
    - Test: test_settings.py
- Deployment specific: site_settings.py

Setting mode
------------

Create a file .app_mode This file would have just one line specifying
settings (and hence app’s) mode.

Valid values are PROD | DEV | TEST 

Based on ``mode`` appropriate settings module would be used (if available)

Overriding settings
-------------------

Defining module veriables in site_settings.py

Example:
--------

**default_settings.py**

``SERVER_PORT = 9999``

**site_settings.py**

``SERVER_PORT = 8888``

Overriding partial settings
---------------------------

Example:

**default_settings.py**

::

    class DB:
      HOST = 'db.example.com'
      PORT = 1234

**site_settings.py**

::

    DB.PORT = 1111