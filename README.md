# power-platform-connectors
This is a repository for Microsoft Power Automate, Power Apps, and Azure Logic Apps connectors

# Table of Contents

- [power-platform-connectors](#power-platform-connectors)
- [Table of Contents](#table-of-contents)
- [How to](#how-to)
  - [Install Custom Connector](#install-custom-connector)
  - [Add custom uality gate](#add-custom-uality-gate)
- [U.K. Government Check VAT](#uk-government-check-vat)
- [WorldTimeAPI](#worldtimeapi)

# How to

Within this repo, there are various MSFCT custom connectors found.

## Install Custom Connector

They are stored through their JSON files, meaning they can't simply be installed as a PowerApps solution ZIP in their current state.
nstead, use the PACONN command line tool:

[Official documentation](https://docs.microsoft.com/en-us/connectors/custom-connectors/paconn-cli)

```
pip install paconn

paconn login

paconn create --api-prop [Path to apiProperties.json] --api-def [Path to apiDefinition.swagger.json] --icon [Path to icon.png]
```

## Add custom uality gate

To make sure, your Custom Connector works as intended, you could create a scheduled flow, running every day (or week) once and calling actions from the connector, tha you want to test against regression.

When set up, simply copy and paste the included `_FlowFailure_Template.json` into your flow, creating a Catch block, that will send an email to you with all details about the failure.

After Copy-Paste, make sure that the "Run After" conition and the outlook connection reference are set correctly for the full Scope.

# U.K. Government Check VAT

Service provided by GOV.UK allowing you to perform unverified and verified checks of UK VAT numbers and view additional details of the VAT registration such as name and address of business.

[More details..](U.K.%20Government%20Check%20VAT/readme.md)

# WorldTimeAPI

WorldTimeAPI is a simple "microservice" which returns the local-time for a given timezone in both unixtime and ISO8601 format. Some additional information is provided, such as whether that timezone is currently in Daylight Savings Time, when DST starts and ends, the UTC offset, etc.

[More details..](WorldTime/readme.md)