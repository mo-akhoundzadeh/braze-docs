---
page_order: 2
nav_title: Parameters
layout: glossary_page
glossary_top_header: "Parameters"
glossary_top_text: "Use these parameters to define your API requests. Though the parameters you need are listed under endpoints, this should give you more insight into their nuance and other specifications."

glossaries:
  - name: App Group REST API Key
    description: The `api_key` indicates the app title with which the data in this request is associated and authenticates the requester as someone who is allowed to send messages to the app. It must be included with every request. It can be found in the Developer Console section of the Braze dashboard.
    field: "api_key"
  - name: App Identifier
    description: If you want to send push to a set of device tokens (instead of users), you need to indicate on behalf of which specific app you are messaging. In that case, you will provide the appropriate App Identifier in a Tokens Object. It can be found in the Developer Console section of the Braze dashboard.
    field: "app_id"
  - name: External User ID
    description: A unique identifier for sending a message to specific users. This identifier should be the same as the one you set in the Braze SDK. You can only target users for messaging who have already been identified through the SDK or the User API. If you need to send messages to specific users who have not yet been identified to Braze, consider attaching a Tokens Object to your message. A maximum of 75 External User IDs are allowed in a request. <br> <br> For campaign trigger endpoints, if you provide this field, the criteria will be layered with the campaign's segments and only users who are in the list of External User IDs and the campaign's segment will receive the message.
    field: "external_user_ids"
  - name: Segment Identifier
    description: The `segment_id` indicates the segment to which the message should be sent. A Segment Identifier for each of the segments you have created can be found in the [Developer Console section of the Braze dashboard. <br> <br> For message endpoints, if you provide both a Segment Identifier _and_ a list of External User IDs in a single messaging request, the criteria will be layered and only users who are in the list of External User IDs _and_ the provided segment will receive the message.
    field: "segment_id"
  - name: Campaign Identifier
    description: For messaging endpoints, the `campaign_id` indicates the API Campaign under which the analytics for a message should be tracked. A Campaign Identifier for each of the campaigns you have created can be found in the Developer Console section of the Braze dashboard. If you provide a Campaign Identifier in the request body, you must provide a `message_variation_id` in each of the message objects indicating the represented variant of your campaign. <br> <br> For campaign trigger endpoints, the `campaign_id` indicates the API ID of the campaign to be triggered. This field is required for all trigger endpoint requests.
    field: "campaign_id"
  - name: Canvas Identifier
    description: For Canvas triggering endpoints, the `canvas_id` indicates the identifier of the Canvas to be triggered or scheduled. This field is required for all trigger endpoint requests.
    field: "canvas_id"
  - name: Send Identifier
    description: For messaging endpoints, the `send_id` indicates the send under which the analytics for a message should be tracked. The `send_id` allows you to pull back analytics for a specific instance of a campaign send via the `sends/data_series` endpoint. API and API trigger campaigns that are sent as a broadcast will automatically generate a send identifier if a send identifier is not provided. <br> <br> If you want to specify your own `send_id`, you'd have to first create one via the `sends/id/create` endpoint. The `send_id` must be all ASCII characters and at most 64 characters long.  You can reuse a send identifier across multiple sends of a same campaign if you want to group analytics of those sends together. <br> <br> Please note that `send_id` tracking is not available for emails sent via Mailjet. <br> <br> Campaign conversions are attributed to the last tracked `send_id` that the user received from that campaign unless the last send the user received was untracked.
    field: "send_id"
  - name: Trigger Properties
    description: "When using one of the endpoints for sending a campaign with API Triggered Delivery, you may provide a map of keys and values to customize your message. If you make an API request that contains an object in `\"trigger_properties\"`, the values in that object can then be referenced in your message template under the `api_trigger_properties` namespace. <br> <br> For example, a request with `\"trigger_properties\" : {\"product_name\" : \"shoes\", \"product_price\" : 79.99}` could add the word \"shoes\" to the message by adding `{{api_trigger_properties.${product_name}}}`."
    field: "trigger_properties"
  - name: Canvas Entry Properties
    description: "When using one of the endpoints for triggering or scheduling a Canvas via the API, you may provide a map of keys and values to customize messages sent by the first steps of your Canvas, in the `\"canvas_entry_properties\"` namespace. <br> <br> For example, a request with `\"canvas_entry_properties\" : {\"product_name\" : \"shoes\", \"product_price\" : 79.99}` could add the word \"shoes\" to a message by adding `{{canvas_entry_properties.${product_name}}}`."
    field: "canvas_entry_properties"
  - name: Broadcast
    description: "When sending a message to a segment or campaign audience using an API endpoint, Braze requires you to explicitly define whether or not your message is a \"broadcast\" to a large group of users by including a \"broadcast\" boolean in the API call. That is, if you intend to send an API message to the entire segment that a campaign or Canvas targets, you must include \"broadcast: true\" in your API call. If the \"broadcast\" flag is not set to true and an explicit list of recipients it not provided, the API endpoint will return an error. Similarly, including \"broadcast: true\" and providing a recipient list will return an error. The \"broadcast\" flag is required in order to protect against accidental sends to large groups of users. <br> <br> Please note that for backwards-compatibility, this field is only required for API calls made for campaigns and Canvases created after August 15, 2017 that intend to send to the entire audience. It will be mandatory on August 31, 2017 for all campaigns and Canvases for API calls that intend to send to the entire audience. The behavior for API calls to deliver campaigns and canvases created prior to these dates is: if an explicit list of recipients is not provided, the message will send to the entire targeted audience of the campaign or Canvas. <br> <br> That is, until 8/15/17, the \"broadcast\" field does not have a default value, so you may wish to explicitly set \"broadcast: false\" in existing API calls. On 8/15/17, it will default to false for newly created Campaigns and Canvases. On 8/31/17, it will default to false for all API calls."
    field: "broadcast"

---
