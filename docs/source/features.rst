Features
=========

For examples on how to add these to the options file, read the :doc:`getting_started` page. Essentially,
add the name of the feature you want to the "features" block. Easy as that! If you want to further customize,
add the relevant options to the "features_customizations" block.

Year/Month Heatmap
--------------------
Shows a heatmap of the frequency of incidents by year (row) and month (column).

**Requires:** latitude_column, longitude_column

**Added with:** `"month_year_heatmap"`

.. image:: images/heatmap.png
    :scale: 75 %
    :align: center

Year Range Map
---------------
Shows the incidents on a world map, with the years shown selected by a range.

**Requires:** latitude_column, longitude_column, time_column

**Added with:** `"yearly_range"`

.. image:: images/yearly_range.png
    :scale: 75 %
    :align: center

One Year Map
--------------
Same as Year Range Map, but for one year at a time.

**Requires:** latitude_column, longitude_column, time_column

**Added with:** `"one_year"`

**Options:**

- "hover_text_columns": Columns whose data you want to show on hovering over a point on the map. Add to `features_customizations` with:

.. code-block:: javascript

    "hover_text_columns": [
            "ColumnName1",
            "ColumnName2:",
            ...
    ],

- "filter_one_year_column": Adds an extra dropdown that lets you only display points which match the selected value of the given column. Added with:

.. code-block:: javascript

     "filter_one_year_column": "ColumnName"

.. image:: images/one_year_range.png
    :scale: 75 %
    :align: center

Month-to-Month Frequency
-------------------------
Histogram showing the frequency per month across all data points.

**Requires:** time_column

**Added with:** `"all_months"`

.. image:: images/all_months.png
    :scale: 75 %
    :align: center

Month-to-Month Frequency for One Year
----------------------------------------
Month-to-Month Frequency, but for one year at a time.

**Requires:** time_column

**Added with:** `"one_year_months"`

.. image:: images/all_months_year.png
    :scale: 75 %
    :align: center

Latitude/Longitude/Time 3D Visualization
-------------------------------------------
A 3D visualization of the data. Latitude, longitude, and time are each a dimension.

**Requires:** time_column

**Added with:** `"threeD"`

.. image:: images/threeD.png
    :scale: 75 %
    :align: center

Points of Interest (POI)
-------------------------------------------
A list of the most popular locations using another dataset to generate the popular locations

**Requires:** latitude_column, longitude_column

**Added with:** `"poi_analysis"`

.. image:: images/poi.png
    :scale: 75 %
    :align: center

Search Key Words
-------------------------------------------
A histogram showing the count of a key term in a specified column

**Requires:** NONE

**Added with:** `"search_columns"`

.. image:: images/search.png
    :scale: 75 %
    :align: center

Bertopic Visualizations
-------------------------------------------
A intertopic map created from BerTopic model. 

**Requires:** description_column

**Added with:** `"nlp_bertopics"`

.. image:: images/bert.png
    :scale: 75 %
    :align: center
