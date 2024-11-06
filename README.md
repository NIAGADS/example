# NIAGADS: Example
example projects leveraging NIAGADS Open Access Software Tools and API endpoints

## About NIAGADS 

The National Institute on Aging Genetics of Alzheimer's Disease Data Storage Site ([NIAGADS](https://www.niagads.org/)) stores and distributes genetics and genomics data from studies on Alzheimer’s disease, related dementias, and aging to qualified researchers globally.

[NIAGADS Open Access](https://www.niagads.org/open-access/) is a collection of files and web-based knowledgebases made available to the public with no data access restrictions. 

## NIAGADS Open Access API

The [NIAGADS Open Access API](https://api.niagads.org) provides programmatic access to the Open Access resources.  

* offers both data and visualization endpoints

### Visualization Endpoints

* Add `format=table` when making requests through a web-browser to display most response in an interactive table
* By default, or explicitly setting `format=json` request will return a traditional `JSON` response

> More visualizations (genome browser, LocusZoom) coming soon.

### Retrive data summaries

* set `content=` to `full`, `summary`, `ids`, `counts` to retrieve different views of the data:
  * `full`: full response
  * `summary`: a brief summary (most informative information) of the response or each record meeting the search criteria
    * for bulk data queries, `summary` will include a count of the number of data points per each matching data track
  * `ids`: a list of record ids matching the search criteria
  * `count`: a count of the number of matchin results; maybe total number of records or in the case of bulk data queries, the number of data points per each matching data track
  
> NOTE: **The API is still under development.**

### Usage examples coming soon

> we apologize for the inconvenience.  Please check back for updates.

*  Endpoints for accessing data in [FILER](https://tf.lisanwanglab.org/FILER/) are now available in beta.  Some FILER queries can return very large response sizes, especially requests to access data (e.g., `/filer/data` routes).  We recommend command-line based request for best performance.  For example:



```bash
curl -X 'GET' '<REQUEST>'  -H 'accept: application/json'
```
