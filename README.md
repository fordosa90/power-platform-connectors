# power-platform-connectors
This is a repository for Microsoft Power Automate, Power Apps, and Azure Logic Apps connectors

# Table of Contents

- [power-platform-connectors](#power-platform-connectors)
- [Table of Contents](#table-of-contents)
- [How to](#how-to)
- [U.K. Government Check VAT](#uk-government-check-vat)
- [WorldTimeAPI](#worldtimeapi)

# How to

Within this repo, there are various MSFCT custom connectors found.
They are stored through their JSON files, meaning they can't simply be installed as a PowerApps solution ZIP in their current state.
nstead, use the PACONN command line tool:

[Official documentation](https://docs.microsoft.com/en-us/connectors/custom-connectors/paconn-cli)

```
pip install paconn

paconn login

paconn create --api-prop [Path to apiProperties.json] --api-def [Path to apiDefinition.swagger.json] --icon [Path to icon.png]
```


# U.K. Government Check VAT

Service provided by GOV.UK allowing you to perform unverified and verified checks of UK VAT numbers and view additional details of the VAT registration such as name and address of business.

[More details..](U.K.%20Government%20Check%20VAT/readme.md)

# WorldTimeAPI

WorldTimeAPI is a simple "microservice" which returns the local-time for a given timezone in both unixtime and ISO8601 format. Some additional information is provided, such as whether that timezone is currently in Daylight Savings Time, when DST starts and ends, the UTC offset, etc.

[More details..](WorldTime/readme.md)