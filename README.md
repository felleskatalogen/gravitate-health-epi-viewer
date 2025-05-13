# gravitate-health-epi-viewer

### Run locally:

#### Using a local FHIR server

1. Set the port for the HAPI FHIR server in the environment variable `FHIR_SERVER_PORT`. Use for example the `.env` file or the `export` command
1. Change the HAPI FHIR server configuration file, `conf/application.yml`:
   a) Comment `server.servlet.context-path`; it should not be set to `/gravitate-health`
   b) Uncomment the value for `hapi.fhir.server_address` that is local and uses `FHIR_SERVER_PORT`
   c) Uncomment the value for `hapi.fhir.tester.home.server_address` that is local and uses `FHIR_SERVER_PORT`
1. Change the apps/config.json
   a) Set `server_url` to the local address, e.g., `http://localhost:8787/fhir`, using the same port that is set in the environment variable
1. Comment out the `ember-gh` service in `docker-compose.yml`

#### Using a remote FHIR server

TODO Subset of the above instructions

#### Known issues

Note on language selection:

'Country' in the overview list in `prodbrowser.html` uses `name[0].usage[0].country.coding[0].display`. N/A appears as country if this element is missing.

The Viewer might show a blank page when such an ePI is opened. There will be content in one of the languages, but the 'Country' column will not indicate which.
