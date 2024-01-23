Appendix C: development log
===========================
v4.0 -> v4.1
^^^^^^^^^^^^
Frontend

* Fixed the blank screen when clicking X/Y profile setting button without images opened ([#2247](https://github.com/CARTAvis/carta-frontend/issues/2247)).
* Removed unused help button for PV preview widget ([#2248](https://github.com/CARTAvis/carta-frontend/issues/2248)).
* Fixed PV preview bug where no PV preview shows up after closing a docked PV preview widget ([#2249](https://github.com/CARTAvis/carta-frontend/issues/2249)).
* Fixed the incorrect deletion of contour levels ([#2251](https://github.com/CARTAvis/carta-frontend/issues/2251)).
* Fixed bug that the frontend crashes when deleting annotations if the export window is opened ([#2278](https://github.com/CARTAvis/carta-frontend/issues/2278)).
* Fixed the performance issue when panning images ([#2291](https://github.com/CARTAvis/carta-frontend/issues/2291)).
* Fixed the crash when plotting online Vizier catalog data ([#2321](https://github.com/CARTAvis/carta-frontend/pull/2321)).
* Fixed missing vector overlays on matched images ([#2293](https://github.com/CARTAvis/carta-frontend/issues/2293)).
* Avoided showing the telemetry dialog temporarily ([#2314](https://github.com/CARTAvis/carta-frontend/issues/2314)).
* Fixed failing to match images spatially ([2252](https://github.com/CARTAvis/carta-frontend/issues/2252)).
* Fixed the delayed start of the program due to telemetry server error ([#2304](https://github.com/CARTAvis/carta-frontend/issues/2304)).

Backend

* Include casacore log messages in carta log ([#1169](https://github.com/CARTAvis/carta-backend/issues/1169)).
* Fixed the problem of opening old IRAM fits images ([#1312](https://github.com/CARTAvis/carta-backend/issues/1312)).
* Fixed scripting interface and symlink directory issues ([#1283](https://github.com/CARTAvis/carta-frontend/issues/1283), [#1284](https://github.com/CARTAvis/carta-frontend/issues/1284), [#1314](https://github.com/CARTAvis/carta-frontend/issues/1314)).
* Fixed incorrect std calculation when fitting images with nan values ([#1318](https://github.com/CARTAvis/carta-backend/issues/1318)).
* Fixed the hanging problem when deleting a region during the spectral profile process ([#1328](https://github.com/CARTAvis/carta-backend/issues/1328)).
* Updated for compatibility with latest carta-casacore using CASA 6.6.0.


v3.0 -> v4.0
^^^^^^^^^^^^
Frontend

* `Closed issues <https://github.com/CARTAvis/carta-frontend/issues?q=is%3Aissue+closed%3A2022-08-23..2023-09-12>`__
* `Merged pull requests <https://github.com/CARTAvis/carta-frontend/issues?q=merged%3A2022-08-23..2023-09-12+>`__

Backend

* `Closed issues <https://github.com/CARTAvis/carta-backend/issues?q=is%3Aissue+closed%3A2022-08-23..2023-09-12+>`__
* `Merged pull requests <https://github.com/CARTAvis/carta-backend/issues?q=merged%3A2022-08-23..2023-09-12+>`__

Controller

* `Closed issues <https://github.com/CARTAvis/carta-controller/issues?q=is%3Aissue+closed%3A2022-08-23..2023-09-12+>`__
* `Merged pull requests <https://github.com/CARTAvis/carta-controller/issues?q=merged%3A2022-08-23..2023-09-12+>`__




v2.0 -> v3.0
^^^^^^^^^^^^
Frontend

* `Closed issues <https://github.com/CARTAvis/carta-frontend/issues?q=is%3Aissue+closed%3A2021-06-07..2022-08-23>`__
* `Merged pull requests <https://github.com/CARTAvis/carta-frontend/issues?q=merged%3A2021-06-07..2022-08-23+>`__

Backend

* `Closed issues <https://github.com/CARTAvis/carta-backend/issues?q=is%3Aissue+closed%3A2021-06-07..2022-08-23+>`__
* `Merged pull requests <https://github.com/CARTAvis/carta-backend/issues?q=merged%3A2021-06-07..2022-08-23+>`__

Controller

* `Closed issues <https://github.com/CARTAvis/carta-controller/issues?q=is%3Aissue+closed%3A2021-06-07..2022-08-23+>`__
* `Merged pull requests <https://github.com/CARTAvis/carta-controller/issues?q=merged%3A2021-06-07..2022-08-23+>`__







v1.4 -> v2.0
^^^^^^^^^^^^
Frontend

* `Closed issues <https://github.com/CARTAvis/carta-frontend/issues?q=is%3Aissue+closed%3A2020-09-17..2021-06-07>`__
* `Merged pull requests <https://github.com/CARTAvis/carta-frontend/issues?q=merged%3A2020-09-17..2021-06-07+>`__

Backend

* `Closed issues <https://github.com/CARTAvis/carta-backend/issues?q=is%3Aissue+closed%3A2020-09-17..2021-06-07+>`__
* `Merged pull requests <https://github.com/CARTAvis/carta-backend/issues?q=merged%3A2020-09-17..2021-06-07+>`__

Controller

* `Closed issues <https://github.com/CARTAvis/carta-controller/issues?q=is%3Aissue+closed%3A2020-09-17..2021-06-07+>`__
* `Merged pull requests <https://github.com/CARTAvis/carta-controller/issues?q=merged%3A2020-09-17..2021-06-07+>`__


v1.3 -> v1.4
^^^^^^^^^^^^
Frontend

* `Closed issues <https://github.com/CARTAvis/carta-frontend/issues?q=is%3Aissue+closed%3A2020-03-31..2020-09-17>`__
* `Merged pull requests <https://github.com/CARTAvis/carta-frontend/issues?q=merged%3A2020-03-31..2020-09-17+>`__

Backend

* `Closed issues <https://github.com/CARTAvis/carta-backend/issues?q=is%3Aissue+closed%3A2020-03-31..2020-09-17+>`__
* `Merged pull requests <https://github.com/CARTAvis/carta-backend/issues?q=merged%3A2020-03-31..2020-09-17+>`__


v1.2 -> v1.3
^^^^^^^^^^^^
Frontend

* `Closed issues <https://github.com/CARTAvis/carta-frontend/issues?q=is%3Aissue+closed%3A2019-08-29..2020-03-31>`__
* `Merged pull requests <https://github.com/CARTAvis/carta-frontend/issues?q=merged%3A2019-08-29..2020-03-31+>`__

Backend

* `Closed issues <https://github.com/CARTAvis/carta-backend/issues?q=is%3Aissue+closed%3A2019-08-29..2020-03-31+>`__
* `Merged pull requests <https://github.com/CARTAvis/carta-backend/issues?q=merged%3A2019-08-29..2020-03-31+>`__


v1.1 -> v1.2
^^^^^^^^^^^^
Frontend

* `Closed issues <https://github.com/CARTAvis/carta-frontend/issues?q=is%3Aissue+closed%3A2019-05-03..2019-08-28>`__
* `Merged pull requests <https://github.com/CARTAvis/carta-frontend/issues?q=merged%3A2019-05-03..2019-08-28+>`__

Backend

* `Closed issues <https://github.com/CARTAvis/carta-backend/issues?q=is%3Aissue+closed%3A2019-05-03..2019-08-28>`__
* `Merged pull requests <https://github.com/CARTAvis/carta-backend/issues?q=merged%3A2019-05-03..2019-08-28+>`__


v1.0 -> v1.1
^^^^^^^^^^^^
Frontend

* `Closed issues <https://github.com/CARTAvis/carta-frontend/issues?q=is%3Aissue+closed%3A2018-12-30..2019-05-02>`__
* `Merged pull requests <https://github.com/CARTAvis/carta-frontend/issues?q=merged%3A2018-12-30..2019-05-02+>`__

Backend

* `Closed issues <https://github.com/CARTAvis/carta-backend/issues?q=is%3Aissue+closed%3A2018-12-30..2019-05-02>`__
* `Merged pull requests <https://github.com/CARTAvis/carta-backend/issues?q=merged%3A2018-12-30..2019-05-02+>`__


