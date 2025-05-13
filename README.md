# gravitate-health-epi-viewer

### Run locally:

#### Using a local FHIR server

1. Set the port on which you want to run the HAPI FHIR server in `docker-compose.yml`, `services.fhir-server.ports`, to one of your preference
1. Change the HAPI FHIR server configuration file, `conf/application.yml`:
   a) Comment `server.servlet.context-path`; it should not be set to `/gravitate-health` 
   b) Set `hapi.fhir.server_address` to the local address, e.g., `http://localhost:8787/fhir`, using the port specified in `docker-compose.yml` above
   c) Set `server_address` in the hapi.fhir.tester with name 'Local tester' to the same local address
1. Change the apps/config.json
   a) Set `server_url` to the local address, e.g., `http://localhost:8787/fhir`
1. Comment out the `ember-gh` service in `docker-compose.yml`

#### Using a remote FHIR server

TODO Subset of the above instructions

#### Known issues

Note on language selection:

'Country' in the overview list in `prodbrowser.html` uses `name[0].usage[0].country.coding[0].display`. N/A appears as country if this element is missing.

The Viewer might show a blank page when such an ePI is opened. There will be content in one of the languages, but the 'Country' column will not indicate which.
