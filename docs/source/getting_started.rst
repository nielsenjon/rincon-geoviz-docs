Getting Started
===================================

Getting your data
------------------

First things first, make sure your data is in a **.csv** format! 
We may handle other file formats in the future, but for now stick with .csv files. The csv data should be row-based, meaning each data point is one row (not column).

For most tools GeoViz provides, you'll need (at least) columns representing:

* Latitude (floats between -90 and 90)
* Longitude (floats between -180 and 180)
* Dates (in a format parseable with pandas' `parse_date functionality <https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.read_csv.html/>`_.)

Setting options
----------------

Next, we'll need to select what components we want to see, as well as tell GeoViz which columns are our latitude/longitude/date columns.
Start by making a `myoptions.json` file that looks like the following:

.. code-block:: json

    {
    "columns": {
        "latitude_column": "latitude",
        "longitude_column": "longitude",
        "time_column": "date"
    }
    }

Where "latitude" is the name of the column of latitude values, "longitude" is the longitude column, and "date" is the column of timestamps.

Now, let's decide which components we want to see! GeoViz has a lot of :doc:`features`, so take some time to look through them.
Let's say that we want to see the **month-to-month frequency** and the **one year map** features. According to the features page, we need to make sure that we have:

- the **time** column for the **month-to-month frequency feature** (done!)
- the **latitude, longitude, and time** columns for the **one year map feature** (also done!)

Now we need to add `all_months` and `one_year` to our options file. Let's do that:

.. code-block:: json

    {
    "columns": {
        "latitude_column": "latitude",
        "longitude_column": "longitude",
        "time_column": "date"
    },
    "features": [
        "all_months",
        "one_year"
    ]
    }

Note that we put `all_months` and `one_year` in the "features" block, separate from the "columns" block. 

If we look at the One Year Map feature, we see that there's some additional options. If we have a column called "victim" whose value
we want to see when we hover over its datapoint, we can add it like so:

.. code-block:: json

    {
    "columns": {
        "latitude_column": "latitude",
        "longitude_column": "longitude",
        "time_column": "date"
    },
    "features": [
        "all_months",
        "one_year"
    ],
    "features_customizations": {
        "hover_text_columns": [
            "victim"
        ],
    },
    }

If we wanted to add a filter column, we could also add it to the "features_customizations" block with

.. code-block:: json

    "features_customizations": {
        "hover_text_columns": [
            "victim"
        ],
        "filter_one_year_column": "victim"
    },
    
.. note::

   Eventually, another json block can be customized: the caching block. Here you can set whether to use 
   cached data for long-running data generation, e.g. Berttopic or POI analysis. It's not implemented yet, but it's on our todo list!

To see what a complete options file looks like, check out the one at `rrcgeoviz/options_tests/devoptions.json <https://github.com/rrc-byu/ds-capstone-2023-2024/blob/major_refactor/tests/options_files/devoptions.json>`_.

Installing & Running GeoViz
----------------------------

That's it for setup, now let's actually see what GeoViz can do. Install it with pip:

.. code-block:: bash

    pip install rrcgeoviz --upgrade

Then we call it from the command line like so:

.. code-block:: bash
    
    rrcgeoviz relative/path/to/mydata.csv relative/path/to/myoptions.json

Make sure that the paths to the data and options are relative to the directory you're calling rrcgeoviz from.

A tab should open in your default browser with GeoViz running! Once you're done, stop the GeoViz server with `Ctrl+C`
in the terminal.
