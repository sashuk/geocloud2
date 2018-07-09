# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](http://keepachangelog.com/en/1.0.0/)
and this project adheres to [Semantic Versioning](http://semver.org/spec/v2.0.0.html).

## [Unreleased]
- Create "retina" tiles option in tile cache settings.

## [2018.1] - 2018-07-5
### Added
- New version 2 of the Elasticsearch API, which acts like the native Elasticsearch search API. Including GET with body and the query string "mini-language".  
- New version 2 of the SQL API, which enables POST and GET of a JSON wrapped query. Supports GET with body.
- New REST "Feature Edit" API, which wraps the WFS-T API in a simple GeoJSON based REST service. Made for JavaScript clients.
- New modern dark theme for Admin.
- Extension mechanism for the REST API. Just drop in code for creating custom APIs.
- SQLite3 and AWS S3 MapCache back-ends are added.
- "Private" tags with prefix "_". These will not be added to CKAN.
- Scheduler has added support for Shape and TAB file sets and zip/rar/gz files over HTTP or FTP.
- Scheduler can now run SQLs before and after a job.
- Scheduler has new option "Download Schema" for GML, so inaccessible schemas can be ignorred.
- Scheduler has a daily email rapport generator. Need a Postmark account.
- Scheduler has a report website at /scheduler/report.php
- Gridded WFS download uses the GMLAS ogr2ogr driver, so schemas are used.
- Gridded WFS download now checks max feature count in single cell and count of duplicates.
- Experimental upload of MS Access databases.
- This change log.


### Changed
- Back-end rewritten for PHP7. 
- MapScript is no longer used.
- Updated routing framework. Routes are now added with full URI paths.
- Better Meta API. Can now be filtered using tags, multiple relation names, schemas and combos. Orders now by sort_id,f_table_name.
- Admin URI is changed from /store to /admin.
- Upgraded QGIS-server to 2.18 LTR. Upload of 2.14 QGS files will still work.
- The advanced layer panel is moved from right side to the left.
- Some rearrangement of buttons.
- Optimized queries for geometry_columns in models.
- Reduced number of API call ind GC2 Admin making it faster.
- HTML title changed to "GC2 Admin"
- MapCache auto expire is now defaulted to 3600 secs., except if cache lock is enabled.
- geocloud.js can now base64 encode the SQL string to avoid filtering in "threat filters". Use base64:true|false in request (true is default).
- Support for Elasticsearch 6.x.
- PG statement timeout in SQL API. Prevent long running statements.
- QGIS project files are stored in database for backup and easy re-creation using a NEW API.
- Better detection of WFS connection string style in QGIS project files.
- QGIS project files names are now randomized, so they don't get overwritten by accident.
- Tags can now be added to existing ones when adding to multiple layers.
- MapCache file is written only when necessary. Making databases with a lot of layers more snappy.
- The MapFile is separated into two MapFiles: One for WMS and one WFS. This way all WFS request uses MapServer and only WMS request will use QGIS Server.

### Deprecated
- Version 1 of the Elasticsearch API
- Version 1 of the SQL API

### Removed

### Fixed
- Data Tab in Admin filters fields with illegal characters.
- Better handling of exceptions in REST API.
- Better handling of strange chars in database relation names.
- A lot of smaller fixes.

### Security
- Better checking of privileges on layers when POSTing WFS GetFeature requests.
