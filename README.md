# API Documentation

## Overview
The ePANDDA public API supports HTTP GET requests for data read operations. ePANNDA is a RESTful web service that returns data in JSON.
The focus of this API is to correlate data from providers ( iDigBio, PaleoBioDB, iDigPaleo) into a single data set that provides utlities
for clustering along various axes ( collection locality, time, collector, collection, current location ) 


* **API Base URL:**
   <br/> `http://search.epandda.org`




**Bibliographic References**
----

ePANNDA bibliographic reference matching takes a fuzzy matching approach to joining iDigBio specimen data to
entered bibliographic reference data from PBDB by using Biological Heritage Library's ( BHL ) API to parse OCR 
text to build a composite score for how closely a specimen matches what is described in the literature.


* **URL**
  <br/> `/api/v1/publication`

* **Method**
  <br/> `GET`

* **URL Params**

  **Required:**
   <br/> `scientific_name`

  **Optional:**
   <br/> `order`
   <br/> `journal`
   <br/> `article`
   <br/> `taxon_auth`
   <br/> `author`
   <br/> `state_prov`
   <br/> `locality`

* **Success Response:**
  * **Code:** 200 <br/>
  **Content:** `{ error: false, msg: "success", data: { // TBD } }`

* **Error Response:**
  * **Code:** 422 UNPROCESSABLE ENTRY <br/>
  **Content:** `ex: { error: true, msg: "missing required parameter", data: {} }`

* **Sample Call:**
   <br/> `ex: http://search.epandda.org/api/v1/publication?taxon_name=cetacea`

* **Notes:**


**Taxonimic Occurrences**
----

ePANNDA occurrence matching will match iDigBio specimen and occurrence data to taxonomic occurrences in PBDB. 
Taxon authority can be passed in to control synonym and accepted name validation 

* **URL**
  <br/> `/api/v1/occurrence`

* **Method**
  <br/> `GET`

* **URL Params**

  **Required:**
   <br/> `taxon_name`
   <br/> `taxon_auth`

  **Optional:**
   <br/> `locality`
   <br/> `period`
   <br/> `institution_code`

* **Success Response:**
  * **Code:** 200 <br/>
  **Content:** `{ error: false, msg: "succes", data: { // TBD } }`

* **Error Response:**
  * **Code:** 422 UNPROCESSABLE ENTRY <br/>
  **Content:** `ex: { error: true, msg: "missing required parameter", data: {} }`

* **Sample Call:**
   <br/> `ex: http://search.epandda.org/api/v1/occurrence?taxon_name=cetacea&taxon_auth=gbif`

* **Notes:**


**Fossil / Modern**
----

ePANNDA fossil / modern matching will look up a taxon name bound by early and late stratographic layer or MYA value.
Taxon tree traversal will attempt to find modern relatives of the fossil species in question.
 
* **URL**
  <br/> `/api/v1/fossilmodern`

* **Method**
  <br/> `GET`

* **URL Params**

  **Required:**
   <br/> `taxon_name`
   <br/> `taxon_auth`
   <br/> `earliest`
   <br/> `latest`

  **Optional:**
   <br/> `locality`

* **Success Response:**
  * **Code:** 200 <br/>
  **Content:** `{ error: false, msg: "succes", data: { // TBD } }`

* **Error Response:**
  * **Code:** 422 UNPROCESSABLE ENTRY <br/>
  **Content:** `ex: { error: true, msg: "missing required parameter", data: {} }`

* **Sample Call:**
   <br/> `ex: http://search.epandda.org/api/v1/fossilmodern?taxon_name=cetacea&taxon_auth=gbif&earliest=paleocene&latest=miocene`

* **Notes:**
