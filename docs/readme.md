# Splunk Community Add-On for UCC Example

This is an example of Technology Add-On (TA) for Splunk built using the [UCC Framework](https://splunk.github.io/addonfactory-ucc-generator/) which demonstrates how to define a modular input to collect data from an API and send it to Splunk.

This Add-On provides a tool to regularly ingest incidents via REST API from [Genesys Cloud System Status](https://status.mypurecloud.com/).

## Features
* API Key validation at configuration
* Poll and ingest the 50 most recent incidents from this [API endpoint](https://status.mypurecloud.com/api/v2#incidents)
* Ingestion of incidents using sourcetype `example:incidents`

## Getting Started
### Installation
Please refer to the [Splunk Documentation](https://docs.splunk.com/Documentation/AddOns/released/Overview/Installingadd-ons) for guidance on installing the Add-On in your environment. The app needs to be installed on the Forwarder tier.

### Configuration
Splunk **admins** will also be requested to:

* Select *Splunk Community Add-on for UCC Example / Configuration* among Splunk UI apps

* Add as many accounts as needed by providing:

  * **Name** of the account (e.g. test)
  * **API Key** to be validated by the server. Must correspond to `super-secret-api-token`

### Usage
After having configured an account:

* Select *Splunk Community Add-on for UCC Example / Inputs* among Splunk UI apps

* Select *Create New Input* and configure your own input(s) by providing:

    * **Name** to identify the input,
    * **Interval** in seconds (i.e. how often do you want to poll data),
    * **Index** that will store data,
    * **Account** to be used to authenticate
    * **Fetch from page** to fetch data from a specific page

* Enable the input to start collecting data

## Troubleshooting
Useful SPL searches to:

* Check on errors occurring at execution `index=_internal sourcetype="splunkcommunity_ta_uccexample_test-*"`

## Versions Supported

* Splunk Enterprise 10.0.0

## Credits & Acknowledgements

This Add-On was built based on the [splunk-example-ta](https://github.com/splunk/splunk-example-ta/tree/main). Thank you a ton to the project maintainers and developers. :heart:

## References
* [UCC Framework Documentation](https://splunk.github.io/addonfactory-ucc-generator/)

## Contributing
See the [CONTRIBUTING.md](https://github.com/splunk-platform-apps/.github/blob/main/.github/CONTRIBUTING.md) file for details.

### Build and Package UCC TAs

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements-dev.txt
ucc-gen build
ucc-gen package --path output/SplunkCommunity_TA_UCCExample
```
