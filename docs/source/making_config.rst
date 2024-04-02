Creating a Config file
==========================

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

.. code-block:: javascript

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

.. code-block:: javascript

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

.. code-block:: javascript

    "features_customizations": {
        "hover_text_columns": [
            "victim"
        ],
        "filter_one_year_column": "victim"
    }
