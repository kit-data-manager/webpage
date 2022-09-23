---
title: Documentation
breadcrumbs: /fairdoscope/documentation/
layout: default
description: Explore the facets of FAIR Digital Objects.
navigation_id: fairdoscope_index
repository_url: https://github.com/kit-data-manager/fairdoscope
repository_name: kit-data-manager/fairdoscope
---

# Usage

<img src="images/fairdoscope-screenshot.png" alt="FAIR-DOscope"/>

Using FAIR-DOscope is relatively straightforward. On the upper left you'll find an input field for typing in PIDs of FAIR DOs.
After clicking the magnifying glass, the PID is resolved, its PID record is presented in the table on the lower left and the
PID graph of (directly) referenced FDOs is drawn to the right.

You may now click a single nodes in the PID graph to navigate to related FDOs. If new relationships are detected, the graph will
be extended dynamically. Alternatively, opening FDO links (marked with a pointer icon) in the table will have the same effect.
Other external links, e.g., links to data types, data, or other digital assets present as URL, are opened in a new browser tab.

Last, but not least, For the PID record table you can switch between two modes:

* Plain Record: Presents the PID record as received from the PID resolving service, which can be used for fast preview.
* Interactive Record: Tries to render table cells according to the detected data type in the PID record.

## Limitations

* Currently, only FAIR DOs following the RDA Recommendations ([Weigel et al.](https://doi.org/10.15497/rda00031)) are properly detected. This requires, that the first key of the PID Record has the value [21.T11148/076759916209e5d62bd5](https://dtr-test.pidconsortium.eu/#objects/21.T11148/076759916209e5d62bd5).
* Currently, only PIDs resolvable via [https://handle.net/](https://handle.net/) are supported
* Data Type resolution is based on the Data Type Registry testing instance hosted at GWDG (see [https://dtr-test.pidconsortium.eu/](https://dtr-test.pidconsortium.eu/))index.markdown

