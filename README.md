# request
Request Handler / Dispatch Controller for Aggregator functionality

## Overview
The ePANDDA public API supports HTTP GET requests for data read operations. ePANNDA is a RESTful web service that returns data in JSON.
The focus of this API is to correlate data from providers ( iDigBio, PaleoBioDB, iDigPaleo) into a single data set that provides utlities
for clustering along various axes ( collection locality, time, collector, collection, current location ) 

##### API Endpoint
`http://search.epandda.org/v0/`

## API Documentation


**Bibliographic References**
----

ePANNDA bibliographic reference matching takes a fuzzy matching approach to joining iDigBio specimen data to
entered bibliographic reference data from PBDB by using Biological Heritage Library's ( BHL ) API to parse OCR 
text to build a composite score for how closely a specimen matches what is described in the literature.


* **URL**
  `/api/v1/publication`

* **Method**
  `GET`

* **URL Params**

  **Required:**
    `scientific_name`

  **Optional:**
    `order`
    `journal`
    `article`
    `taxon_auth`
    `author`
    `state_prov`
    `locality`

* **Success Response:**
  * **Code:** 200 <br/>
  **Content:** `{ // TBD }`

* **Error Response:**
  * **Code:** 422 UNPROCESSABLE ENTRY <br/>
  **Content:** `ex: { error: "missing required parameter"}`

* **Sample Call:**

* **Notes:**
