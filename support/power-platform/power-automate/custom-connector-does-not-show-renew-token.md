---
title: Custom Connector with Oauth 2.0 does not show Refresh URL  
description: User cannot see current renew token configuration for custom connector on the GUI or swagger editor.
ms.author: edsanchez
ms.topic: Power Platform Custom Connector
ms.date: 06-07-2021 
---
# Custom Connector with Oauth 2.0 does not show "Refresh URL"

_Applies to:_ &nbsp; Power Automate, Custom Connectors

Custom connector maintenance and troubleshooting may require to review current configuration to verify values or made
changes to the actual connector configuration’s like Connector Name,  Client Id, Client Secret, Authorization URL,
Token URL, Refresh URL, Scope, Redirect URL or specific connector definitions.

For custom connectors using generic Oauth 2.0 you cannot see the "Refresh URL" value that you configure for the
connector.

## Symptoms

For Custom connectors using Oauth 2.0 you cannot verify the current value for Refresh URL.
This value is under the security configuration for the custom connector with Oauth 2.0 authentication and specify the
URL to use for renewing the Oauth token.

Developers will expect to see the current security Oauth configuration in case the connector doesn’t work, and platform
shows a “Refresh URL” text instead the current Refresh URL value.

Because of that, developers can’t verify the current Refresh URL value on the graphic editor or in the swagger editor
and can lose time trouble shooting security configurations.

### Graphic configuration showing the “Refresh URL” value instead the real Refresh URL

![Image 1. Sample Image showing connector security tab configuration ](media/custom-connector-does-not-show-renew-token/tokenrefresh-url.JPG)

### Swagger Editor don’t show the Refresh URL value and don’t allow you to add the value

![Image 2. Sample Image showing connector security tab configuration swagger editor](media/custom-connector-does-not-show-renew-token/oauth2-swagger-security.JPG)

## Cause

This is a cosmetic error, if you update the value that configuration remain on the platform but you cannot see it,
and it does not affect the Refresh URL process.

## Resolution

Since it is a cosmetic error, if you need to update the security configuration for the connector you can add all values
including the current “Refresh URL” to the Custom Connector and save all the latest configuration values, those changes
will be applied to the connector, the only value that you can not see after you save changes will be the “Refresh URL”
but platform works with the latest value you save to the connector configuration.

## More information

For more information see:

[Custom Connector Connection Parameters Oauth 2.0](https://docs.microsoft.com/connectors/custom-connectors/connection-parameters#oauth-20)
