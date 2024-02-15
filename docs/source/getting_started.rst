Getting Started
===================================

Getting your data
------------------

First things first, make sure your data is in a **.csv** format! 
We may handle other file formats in the future, but for now stick with .csv files. The csv data should be row-based, meaning each data point is one row (not column).

For most tools GeoViz provides, you'll need (at least) columns representing:
- Latitude (floats between -90 and 90)
- Longitude (floats between -180 and 180)
- Dates (in a format parseable with pandas' `parse_date functionality <https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.read_csv.html/>`_.)

Setting options
----------------

Next, we'll need to select what components we want to see, as well as tell GeoViz which columns are our latitude/longitude/date columns.
Start by making a `myoptions.json` file that looks like the following:

.. code-block:: json

    {
    "latitude_column": "latitude",
    "longitude_column": "longitude",
    "time_column": "date",
    }

Where "latitude" is the name of the column of latitude values, "longitude" is the longitude column, and "date" is the dates column.

Now, let's decide which components we want to see! GeoViz has a lot of :doc:`features`, so take some time to look through them.
Let's say that we want to see the temporal heatmap. We can see that to enable that, we need to make sure the latitude & longitude columns are set (done!) 
and that we need is to add `yearly_range` to our options file. Let's do that:

.. code-block:: json

    {
    "latitude_column": "latitude",
    "longitude_column": "longitude",
    "time_column": "date",
    "yearly_range": true
    }

Installing & Running GeoViz
----------------------------

That's it for setup, now let's actually see what GeoViz can do. Install it with pip:

.. code-block:: bash

    pip install rrcgeoviz --upgrade

Then we call it from the command line like so:

.. code-block:: bash
    
    rrcgeoviz relative/path/to/mydata.csv --options relative/path/to/myoptions.json

Make sure that the paths to the data and options are relative to the directory you're calling rrcgeoviz from.

.. note::

   Some warnings may appear in the console. Ignore these: we're in the process of fixing them.

A tab should open in your default browser with GeoViz running! Once you're done, stop the GeoViz server with `Ctrl+C`
in the terminal.
