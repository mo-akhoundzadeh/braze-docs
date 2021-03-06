---
nav_title: April
page_order: 9
---

# April 2019

## New Currents Events & Fields

In addition to some corrections to the section, a new [Subscription Event]({{ site.baseurl}}/partners/braze_currents/data_storage_events/message_engagement_events/#subscription-events) has been added to the Message Engagement Events page. You can now export Subscription Group State Change data from Braze to [Segment]({{ site.baseurl}}/partners/technology_partners/data_and_infrastructure_agility/customer_data_platform/segment_for_currents/#integration-details) and [mParticle]({{ site.baseurl}}/partners/technology_partners/data_and_infrastructure_agility/customer_data_platform/mparticle_for_currents/#integration-details), as well as that and Install Attribution Events in [Mixpanel]({{ site.baseurl}}/partners/technology_partners/insights/behavioral_analytics/mixpanel_for_currents).

Additionally, the property `canvas_step_id` has been added to available [Conversion Events]({{ site.baseurl}}/partners/braze_currents/data_storage_events/message_engagement_events/#conversion-events).

{% alert important %}
To take advantage of these updates, you will need to edit your Currents connector settings and enable the events you want to use. Reach out to your account manager if you have any questions.
{% endalert %}

## Subscription Groups Archiving

You can now [archive Subscription Groups]({{ site.baseurl}}/user_guide/message_building_by_channel/email/managing_user_subscriptions/#archiving-groups)! Archived Subscription Groups cannot be edited and will no longer appear in Segment Filters.  If you attempt to archive a group which is being used as a Segment Filter in any email, campaign, or canvas, you will receive an error message that will prevent you from archiving the Group until you remove all usages of it.
