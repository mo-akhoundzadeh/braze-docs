---
nav_title: Customer Behavior Events
page_order: 2
---


# Customer Behavior Events

These schema include other App or Website activity such as Sessions, Custom Events, and Purchases tracked through the platform.

Please contact your Account Manager or [open a support ticket][support] if you need access to additional event entitlements.


{% alert important %}
Please note that these schema __only apply to the flat file event data we send to Data Warehouse partners (Google Cloud Storage, Amazon S3, and Microsoft Azure Blob Storage)__. For schema that apply to the other partners, please check [their respective pages]({{ site.baseurl }}/partners/braze_currents/integration/available_partners/).
{% endalert %}


{% details CUSTOM EVENTS %}

Data accumulates when a user performs a custom event. Use this to track users who perform custom events in your app.

```json
// Custom Event: users.behaviors.CustomEvent
{
  "id": (string) unique id of this event,
  "user_id": (string) braze user id of the user,
  "external_user_id": (string) External ID of the user,
  "time": (int) time of the event in seconds since the epoch,
  "timezone": (string) IANA timezone of the user at the time of the event,
  "name": (string) name of the custom event,
  "app_id": (string) id for the app on which the user action occurred,
  "platform": (string) platform of the device (iOS, Android, web, etc.),
  "os_version": (string) os version of device used for the action,
  "device_model": (string) hardware model of the device,
  "device_id": (string) id of the device on which the event occurred,
  "properties": (string) JSON encoded string of the custom properties for this event
}
```

{% enddetails %}

{% details PURCHASE EVENTS %}

Data accumulates when a user makes a purchase. Use this data to track when users purchase something in the app.

{% alert tip %}
Purchases are special custom events, and come with a JSON encoded string of custom event properties the same way custom events do.
{% endalert %}

```json
// Purchase Event: users.behaviors.Purchase
{
  "id": (string) unique id of this event,
  "user_id": (string) braze user id of the user,
  "external_user_id": (string) External ID of the user,
  "time": (int) time of the event in seconds since the epoch,
  "product_id": (string) id of the product purchased,
  "price": (float) price of the purchase,
  "currency": (string) three letter alpha ISO 4217 currency code,
  "properties": (string) JSON encoded string of the custom properties for this event,
  "app_id": (string) id for the app on which the user action occurred,
  "platform": (string) platform of the device (iOS, Android, web, etc.),
  "os_version": (string) os version of device used for the action,
  "device_model": (string) hardware model of the device,
  "device_id": (string) id of the device on which the event occurred
}
```
{% enddetails %}


{% details SESSION EVENTS %}

Data accumulates when a user triggers session events. Use this data to track when users start and end sessions.

{% alert tip %}
When a user starts their first session, both a `FirstSession` and a `SessionStart` event are fired.
{% endalert %}

```json
// Session Start: users.behaviors.app.FirstSession
{
  "id": (string) unique id of this event,
  "user_id": (string) braze user id of the user,
  "external_user_id": (string) External ID of the user,
  "time": (int) time of the event in seconds since the epoch,
  "timezone": (string) IANA timezone of the user at the time of the event,
  "session_id": (string) id of the session,
  "app_id": (string) id for the app on which the user action occurred,
  "platform": (string) platform of the device (iOS, Android, web, etc.),
  "os_version": (string) os version of device used for the action,
  "device_model": (string) hardware model of the device,
  "device_id": (string) id of the device on which the session occurred
}

// Session Start: users.behaviors.app.SessionStart
{
  "id": (string) unique id of this event,
  "user_id": (string) braze user id of the user,
  "external_user_id": (string) External ID of the user,
  "time": (int) time of the event in seconds since the epoch,
  "session_id": (string) id of the session,
  "app_id": (string) id for the app on which the user action occurred,
  "platform": (string) platform of the device (iOS, Android, web, etc.),
  "os_version": (string) os version of device used for the action,
  "device_model": (string) hardware model of the device,
  "device_id": (string) id of the device on which the session occurred
}

// Session End: users.behaviors.app.SessionEnd
{
  "id": (string) unique id of this event,
  "user_id": (string) braze user id of the user,
  "external_user_id": (string) External ID of the user,
  "time": (int) time of the event in seconds since the epoch,
  "session_id": (string) id of the session,
  "duration": (float) seconds session lasted,
  "app_id": (string) id for the app on which the user action occurred,
  "platform": (string) platform of the device (iOS, Android, web, etc.),
  "os_version": (string) os version of device used for the action,
  "device_model": (string) hardware model of the device,
  "device_id": (string) id of the device on which the session occurred
}
```
{% enddetails %}

{% details LOCATION EVENTS %}

Data accumulates when a user triggers a location event. Use this to track users triggering location events in your app.

```json
// Location Event: users.behaviors.Location
{
  "id": (string) unique id of this event,
  "user_id": (string) braze user id of the user,
  "external_user_id": (string) External ID of the user,
  "time": (int) time of the event in seconds since the epoch,
  "longitude": (float) longitude of recorded location,
  "latitude": (float) latitude of recorded location,
  "altitude": (float) altitude of recorded location,
  "ll_accuracy": (float) latitude/longitude accuracy of recorded location,
  "alt_accuracy": (float) altitude accuracy of recorded location,
  "app_id": (string) id for the app on which the user action occurred,
  "platform": (string) platform of the device (iOS, Android, web, etc.),
  "os_version": (string) os version of device used for the action,
  "device_model": (string) hardware model of the device,
  "device_id": (string) id of the device on which the event occurred
}
```
{% enddetails %}

{% details NEWS FEED EVENTS %}

Data accumulates when a user views the News Feed. This is when the user views the entire news feed, not a specific News Feed Card. Use this to track users viewing the News Feed.

{% alert tip %}
We do track other News Feed events; these are located in [Message Engagement Events](]({{ site.baseurl }}partners/braze_currents/data_storage_events/message_engagement_events/).
{% endalert %}

```json
// News Feed Impression: users.behaviors.app.NewsFeedImpression
{
  "id": (string) unique id of this event,
  "user_id": (string) braze user id of the user,
  "external_user_id": (string) External ID of the user,
  "time": (int) time of the event in seconds since the epoch,
  "app_id": (string) id for the app on which the user action occurred,
  "platform": (string) platform of the device (iOS, Android, web, etc.),
  "os_version": (string) os version of device used for the action,
  "device_model": (string) hardware model of the device,
  "device_id": (string) id of the device on which the event occurred
}
```

{% enddetails %}

{% details UNINSTALL EVENTS %}

Data accumulates when a user uninstalls an app. Use this data to track when users uninstall an app.

{% alert important %}
Please note that this is not fired when the user actually uninstalls the app - that's impossible to track exactly. Braze sends a daily silent push to determine if the app still exists on your user's device, and if we get an error on that silent push, it is assumed the app has been uninstalled.
{% endalert %}

```json
// Uninstall Event: users.behaviors.Uninstall
{
  "id": (string) unique id of this event,
  "user_id": (string) braze user id of the user,
  "external_user_id": (string) External ID of the user,
  "time": (int) time of the event in seconds since the epoch,
  "app_id": (string) id for the app on which the user action occurred
}
```

{% enddetails %}

{% details ATTRIBUTION EVENTS %}

Data accumulates when an app installation is attributed to a source. Use this to track where your app installs are coming from.

```json
// Install Attribution Event: users.behaviors.InstallAttribution
{
  "id": (string) unique id of this event,
  "user_id": (string) braze user id of the user,
  "external_user_id": (string) External ID of the user,
  "time": (int) time of the event in seconds since the epoch,
  "source": (string) the source of the attribution
}
```
{% enddetails %}

[support]: {{ site.baseurl }}/support_contact/
