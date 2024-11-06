# example
example projects leveraging NIAGADS Open Access Software Tools and API endpoints

> This documentation and example code is still under development.  We apologize for the inconvenience.  Please check back by 11/11/2024 for more in depth usage examples for the *NIAGADS Open Access API*

## NIAGADS Open Access API

> The NIAGADS Open Access API provides programmatic access to unrestricted data resources at the NIAGADS repository.  More information coming soon.

Documentation available at: <https://api.niagads.org>

*  Endpoints for accessing data in [FILER](https://tf.lisanwanglab.org/FILER/) are now available in beta.  Some FILER queries can return very large response sizes, especially requests to access data (e.g., `/filer/data` routes).  We recommend command-line based request for best performance.  For example:

> Request all data points contained in histone modifications tracks in the brain, in the region of the ABCA7 gene:
```bash
curl -X 'GET' ''  -H 'accept: application/json'
```
