# NIAGADS: Example
example projects leveraging NIAGADS Open Access Software Tools and API endpoints

## About NIAGADS 

The National Institute on Aging Genetics of Alzheimer's Disease Data Storage Site ([NIAGADS](https://www.niagads.org/)) stores and distributes genetics and genomics data from studies on Alzheimer’s disease, related dementias, and aging to qualified researchers globally.

[NIAGADS Open Access](https://www.niagads.org/open-access/) is a collection of files and web-based knowledgebases made available to the public with no data access restrictions. 

## NIAGADS Open Access API

The [NIAGADS Open Access API](https://api.niagads.org) provides programmatic access to the Open Access resources.  Follow the provided link to browse the API documentation and OpenAPI specification.

* offers both data and visualization endpoints

> NOTE: **The API is still under development.**

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
  
### Example Usage

> More in-depth usage examples coming soon; we apologize for the delay.  Please check back for updates.

*  Endpoints for accessing data in [FILER](https://tf.lisanwanglab.org/FILER/) are now available in beta.  Some FILER queries can return very large response sizes, especially requests to access data (e.g., `/filer/data` routes).  We recommend command-line based request for best performance if you want a JSON response.  For example:

### Find data tracks that meet search criteria (biosample, feature type, analysis or assay type, etc)

> Find all `QTL` tracks in `brain` tissue:

```bash
curl -X 'GET' 'https://api.niagads.org/filer/metadata/search?keyword=QTL&filter=biosample+eq+brain&content=full&format=json' -H 'accept: application/json'
```

> In a browser window, do the same, but view the results in an interactive table:

<https://api.niagads.org/filer/metadata/search?keyword=QTL&filter=biosample+eq+brain&content=full&format=table>

* from the table, you can sort, filter (column filters coming soon), and export the table data in various formats
* change the `content` to `summary` for a brief response (usefully for quickly browsing or to reduce the size of the response

<https://api.niagads.org/filer/metadata/search?keyword=QTL&filter=biosample+eq+brain&content=summary&format=table>

* or `content=counts` to just get the total number of tracks that met your search criteria:

<https://api.niagads.org/filer/metadata/search?keyword=QTL&filter=biosample+eq+brain&content=counts&format=json>

* or `content=ids` to just get a list of the unique FILER identifiers for the tracks that met the search criteria

<https://api.niagads.org/filer/metadata/search?keyword=QTL&filter=biosample+eq+brain&content=ids&format=json>

### Explore track data

You can also explore track data directly.

For example let's retrieve all histone modifications in the span of the gene `ABCA7` (coming soon - ability to use gene symbols and variant ids as locus) in astrocytes.  

> Note: This feature is under development.  Some queries may return a lot of data and the proxy may time out.  We are working to determine how best to limit or page request sizes.  Thank you for understanding.

Return a `full` response (all the the data points):

```bash
curl -X 'GET' 'https://api.niagads.org/filer/data/search?keyword=astrocyte&loc=chr19%3A1038997-1066572&filter=feature+eq+histone_modification&content=full&format=json' -H 'accept: application/json'
```

> For real-time data mining and browsing, choose to return the content as a `summary` (`content=summary`)

<https://api.niagads.org/filer/data/search?keyword=astrocyte&loc=chr19%3A1038997-1066572&filter=feature+eq+histone_modification&content=summary&format=table>

* you can also get this response in `JSON` by setting `format=json`.  From the command line, you could run:
* summary tables allow users to select rows and view just the data on the selected track(s), either in a table or in a Genome Browser view.
