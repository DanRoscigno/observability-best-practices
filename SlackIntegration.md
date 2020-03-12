Add to Elasticsearch User Settings in Elasticsearch Service on Elastic Cloud:

```
xpack.notification.slack:
  default_account: alerts
  account:
    alerts:
      message_defaults:
        from: alerts
        to: dev
```

Notes:
 - `alerts`: A Slack accountname.  You do not need a real Slack 
account with the name `alerts`, the messages will appear to come 
from an account named `alerts`.
 - `default_account: alerts`: If there were multiple account names
defined here then `alerts` would be the default.  Declare a default
even if there is only one in case more get added later.
 - `to: dev`: The destination Slack channel for the alerts is `#dev`

Add a Slack Webhook to the Elasticsearch keystore with a key name
corresponding to the Slack account specified above:

Name: `xpack.notification.slack.account.ACCOUNT_NAME.secure_url`
(using the above example Slack account, the ACCOUNT_NAME would be
set to `alerts`:
`xpack.notification.slack.account.alerts.secure_url`

Secret: The Webhook URL, which you can get by clicking on Settings > 
Add an App in your Slack channel and then searching for Webhook

