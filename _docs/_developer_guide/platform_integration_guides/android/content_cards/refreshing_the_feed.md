---
nav_title: Refreshing the Feed
page_order: 3
search_rank: 5
platform: Android
---
## Refreshing Content Cards

You can queue a manual refresh of the Braze Content Cards at any time by calling:

{% tabs %}
{% tab JAVA %}

```java
Appboy.getInstance(context).requestContentCardsRefresh();
```

{% endtab %}
{% tab KOTLIN %}

```kotlin
Appboy.getInstance(context).requestContentCardsRefresh()
```

{% endtab %}
{% endtabs %}
