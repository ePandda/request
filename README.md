# request
Request Handler / Dispatch Controller for Aggregator functionality

## Overview
The ePANDDA public API supports HTTP GET requests for data read operations. ePANNDA is a RESTful web service that returns data in JSON.
The focus of this API is to correlate data from providers ( iDigBio, PaleoBioDB, iDigPaleo) into a single data set that provides utlities
for clustering along various axes ( collection locality, time, collector, collection, current location ) 

##### API Endpoint
`http://search.epandda.org/v0/`


## Search

##### Basic Searching
Searching of correlated data is accessed from the following endpoints:

``` 
GET /v0/search?locality= 
GET /v0/search?time=
GET /v0/search?collector=
GET /v0/search?collection=
GET /v0/search?location=
```

## Fuzz Factor
Users can control the degree of fuzzy matching determining what defines a "match" from ensuring exact specimen is cited in literature up to
various levels of the taxonomic hierarchy
