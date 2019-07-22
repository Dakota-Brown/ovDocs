# Tray Documentation

## Getting Started

## Triggers
Tray's Documentation on Triggers is pretty good. See the links below for general descrptions and examples of how they work. I'll be adding examples of how we use them as I go along.

* Callable Trigger
	* [Callable Trigger](https://tray.io/documentation/platform/connectors/docs/triggers/callable-trigger/).<br/>
	This trigger is used when the workflow is called from another workflow. This is especially useful in passing api tokens and other data that you would otherwise not be able to obtain within Tray.
* Email Trigger
	* [Email Trigger](https://tray.io/documentation/platform/connectors/docs/triggers/email-trigger/)
* Form Trigger
	* [Form Trigger](https://tray.io/documentation/platform/connectors/docs/triggers/form-trigger/)
* Manual Trigger
	* [Manual Trigger](https://tray.io/documentation/platform/connectors/docs/triggers/manual-trigger/).<br/>
	This is a trigger that you manually start for the workflow to run.
* Scheduled Trigger
	* [Scheduled Trigger](https://tray.io/documentation/platform/connectors/docs/triggers/scheduled-trigger/)
* Webhook Trigger
	* [Webhook Trigger](https://tray.io/documentation/platform/connectors/webhook-trigger/)

## Core
**Boolean Condition**<br/>
OP - It allows you to make boolean comparisons between various types of data.<br/>
OP - It also allows you to check if a property exists whether it be a string or a jsonPath.<br/>
[Video](https://youtu.be/nrVrSn9dsf4)
___
**Branch**<br/>
If the value to test matches the imported data into the branch step, then find and start the branch that matches that matched value.
You can have as many branches as you need.
___
**Break Loop**<br/>
This breaks a loop.
___
**CSV Editor**<br/>
This is best used when manipulating CSV files.
This allows you to import or create a CSV file which is a tabular data sheet, such as a sheets export.
The CSV Reader and CSV Editor cannot be used interchangeably.<br/><br/>
When you create a CSV using the CSV Editor it will only be available to modify during the current workflow run. If you want to use it across workflow runs, you need to export it to a persistent file at the end so it can be re-imported on the next run.
<br/><br/>[Extensive Help Article](https://tray.io/documentation/platform/connectors/docs/core/csv-processor/?docs_source=search&docs_term=csv%20editor#create-from-file)
___
**CSV Reader**<br/>
This is best used when querying from CSV files rather than changing them.
The CSV Reader and CSV Editor cannot be used interchangeably.
___
**Call Workflow**<br/>
This enables you to call a separate workflow.
Crucially it allows you to transfer data such as API keys and tokens out of and into other workflows where this is otherwise not possible.
Aside from that, it is the go to tool for separating workflows, especially if one workflow can be called by multiple other workflows.
___
**Data Mapper**<br/>
Allows you to map and configure individual data points that are being pulled from one service into another one.
You are pulling data from a service and need the results to be formatted so as to update a particular field in a database with a value that is more helpful for the users of the database (e.g. 'landline call' and 'cellphone call' could both be mapped to 'phone call').<br/><br/>
 The Data Mapper has a Map Data operation for this purpose.You wish to automatically pass data from one service to another by specifying a mapping 'table' so that e.g. the 'name' field in Service 1 is automatically mapped to the 'item' field in Service 2. The Data Mapper has a Map Fields operation for this purpose.

[Extensive Help Article](https://tray.io/documentation/platform/connectors/docs/core/data-mapper/?docs_source=search&docs_term=data%20mapper)
___
**Data Storage **<br/>
The "Data Storage" connector on Tray allows you to set and get arbitrary data, or perform more complex operations on lists and objects. It works using a key-value store, which means that you can set any type of value you like, using a key to retrieve it. At its core, Data Storage can allow you to work with local variables, easily share data between multiple steps in a custom way, pass data between workflow executions, or even multiple workflows.

[Extensive Help Article](https://tray.io/documentation/platform/connectors/docs/core/data-storage/?docs_source=search&docs_term=data%20storage)
___
**Delay**<br/>
Allows you to add a delay in between steps.
___
**FTP Client**<br/>
The FTP Client allows you to list, upload and download files on an FTP server.
 <br/><br/>[Extensive Help Article](https://tray.io/documentation/platform/connectors/docs/core/ftp-client/?docs_source=search&docs_term=ftp)
___
**HTTP Client Connector**<br/>
Make calls to any REST API
You can use the HTTP client to make calls to any REST API; it's useful for making calls to services that don't yet have a tray connector.
 <br/><br/>[Extensive Help Article](https://tray.io/documentation/platform/connectors/http-client/?docs_source=search&docs_term=http)
___
**Loop**<br/>
You can loop through lists.
You can loop forever. You can loop through an object<br/>
The question about whether to use a list or an object really depends on whether you need to process all of the items every time (use a list) or if you ever need to only access one of the items (use an object).<br/><br/> **Example:** If trying to pull all of the partner client_support Slack channel IDs, you can loop through a list pulling all of the ids and then pulling the client_support ones out of that. Or, with an object loop, you can just pull the client_support channel ID from each partner.

[Extensive Help Article](https://tray.io/documentation/platform/connectors/docs/core/loop/?docs_source=search&docs_term=loop)
___
**Mustache Template**<br/>
Use mustache templating to substitute variables into a HTML template.<br/>
(Requires Further Research).
___
**Script**<br/>
This allows you to write custom scripts while interacting with Tray values, connectors, and services.

[Extensive Help Article](https://tray.io/documentation/platform/connectors/docs/core/script/?docs_source=search&docs_term=script)
___
**Send Email**<br/>
Allows you to send an email.
A key part of this is the ability to pass in data from steps in Tray to the actual email content using step data variables such as 

	Billing Team,<br>
	Please update your billing information so that <b>all billable time for the below client/site reflects your discounted premium hourly rates:</b>

	First Name: {$.steps.trigger.payload.subscription.customer.first_name}
	Last Name: {$.steps.trigger.payload.subscription.customer.last_name}
	Email: {$.steps.trigger.payload.subscription.customer.email}

	Address: {$.steps.trigger.payload.subscription.customer.address}
	City: {$.steps.trigger.payload.subscription.customer.city}
	State: {$.steps.trigger.payload.subscription.customer.state}
	Zip: {$.steps.trigger.payload.subscription.customer.zip}

	Product: {$.steps.trigger.payload.subscription.product.name}
	Status: {$.steps.trigger.payload.subscription.state}

	The OneVision RMR Team
 The above template is in the {TEMPLATE}: Chargify Subscription v3.6.3 - w/callable workflow labeled as the Premium Billing Notification.
___
**Terminate**<br/>
Allows you to terminate or stop a tray workflow.
___
**Trigger Event Reply**<br/>

The Trigger Event Reply can be used when a reply is needed for your workflow trigger. It is used to signal to the trigger that it should finish what it is doing, stop waiting and process the reply data sent to it from the Trigger Event Reply.
An example of when you might want to do this is, after taking several steps to process the data received via the webhook trigger, you may wish to respond with a 200 status and a "Successfully Recorded" message in the body.
Or, after making an unsuccessful boolean check for a user or valid url, you may wish to respond with a 404 'not found' message.<br/>

A good place to use this is on the false or failed side of a boolean condition to return a detailed response on what data or process did not match in order to be successful.

[Extensive Help Article](https://tray.io/documentation/platform/connectors/docs/core/trigger-event-reply/?docs_source=search&docs_term=trigger)
___
**XML Decoder**<br/>
This decodes XML.
___
## Authentications
Authentications are how you connect the different services with Tray. 
___
**Adding Authentications**<br/>
___
**Passing Authentications Between Workflows**<br/>
This is key to transferring api keys, tokens, and other information only available within authentications.
This requires two workflows to accomplish.

* One to call and catch the authentication and then pass it into a call workflow step.
* Once in the workflow that was called, you can pull the authentication data from the trigger.