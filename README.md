# power-platform-connectors
This is a repository for Microsoft Power Automate, Power Apps, and Azure Logic Apps connectors

# NOT PUSHING NEW CONNECTORS HERE AS SUBMITTING THEM AS INDEPENDENT PUBLISHER TO MSFT

[https://github.com/microsoft/PowerPlatformConnectors/tree/dev/independent-publisher-connectors](https://github.com/microsoft/PowerPlatformConnectors/tree/dev/independent-publisher-connectors)

# Table of Contents

- [power-platform-connectors](#power-platform-connectors)
- [NOT PUSHING NEW CONNECTORS HERE AS SUBMITTING THEM AS INDEPENDENT PUBLISHER TO MSFT](#not-pushing-new-connectors-here-as-submitting-them-as-independent-publisher-to-msft)
- [Table of Contents](#table-of-contents)
- [How to](#how-to)
  - [Create new Custom Connector](#create-new-custom-connector)
  - [Install Custom Connector](#install-custom-connector)
  - [Add custom Quality gate](#add-custom-quality-gate)
  - [Install test flows](#install-test-flows)
  - [Create canvas from Connector](#create-canvas-from-connector)
- [Google Books](#google-books)
- [U.K. Government Check VAT](#uk-government-check-vat)
- [WorldTimeAPI](#worldtimeapi)

# How to

Within this repo, there are various MSFCT custom connectors found.

## Create new Custom Connector

There are multiple ways to create a new custom connector, below are the steps for the most manual process.

1. Navigate to flow.microsoft.com
2. Create a new solution and a new Custom Connector
3. Define all properties (details, security, operations) and save
4. Test the operations by first creating a connection
5. Download the connector definition as follows:

```
pip install paconn

paconn login

paconn download --env [Environment ID] --dest [Destination directory]
```

## Install Custom Connector

They are stored through their JSON files, meaning they can't simply be installed as a PowerApps solution ZIP in their current state.
nstead, use the PACONN command line tool:

[Official documentation](https://docs.microsoft.com/en-us/connectors/custom-connectors/paconn-cli)

```
pip install paconn

paconn login

paconn create --env [Environment ID] --api-prop [Path to apiProperties.json] --api-def [Path to apiDefinition.swagger.json] --icon [Path to icon.png]
```

## Add custom Quality gate

To make sure, your Custom Connector works as intended, you could create a scheduled flow, running every day (or week) once and calling actions from the connector, tha you want to test against regression.

When set up, simply copy and paste the included `_FlowFailure_Template.json` into your flow, creating a Catch block, that will send an email to you with all details about the failure.

After Copy-Paste, make sure that the "Run After" conition and the outlook connection reference are set correctly for the full Scope.

## Install test flows

There are test flows implemented for my custom connectors already. They:
  - run daily
  - execute happy path for all actions
  - send me email when failure happens

Contents are found in `src` folder, and can be installed as follows:

```
pac solution pack --zipfile [ZIP Path] --folder [Folder Path] --packagetype 'Both'

pac solution unpack --zipfile [ZIP Path] --folder [Folder Path] --packagetype 'Both'
```

## Create canvas from Connector

In case you have a custom connector - not native - you can have an easy headstart to build a canvas app using it: [Documentation](https://learn.microsoft.com/en-us/power-platform/developer/cli/reference/canvas#pac-canvas-create)

```
pac auth create 
pac auth list
pac auth update --index {index} --name {instancename} --environment {instanceID}
pac auth select --index {index}
cd {folder path to drop msApp}
pac canvas create --msapp {HelloWorld.msapp} --connector-display-name {connectorName}
```

# Google Books

Google Books provides and open and public library enabling searching information of various volumes while also providing a way to search within publications.

[More details..](Google%20Books/readme.md)

# U.K. Government Check VAT

Service provided by GOV.UK allowing you to perform unverified and verified checks of UK VAT numbers and view additional details of the VAT registration such as name and address of business.

[More details..](U.K.%20Government%20Check%20VAT/readme.md)

# WorldTimeAPI

WorldTimeAPI is a simple "microservice" which returns the local-time for a given timezone in both unixtime and ISO8601 format. Some additional information is provided, such as whether that timezone is currently in Daylight Savings Time, when DST starts and ends, the UTC offset, etc.

[More details..](WorldTime/readme.md)