---
group: product-recommendations
title: Integrate Product Recommendations into your Headless Storefront
ee_only: True
---

You can integrate Product Recommendations in a headless storefront using either [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/) or a custom frontend technology, such as React or Vue JS.

Product Recommendations require [behavioral and catalog data]({{ page.baseurl }}recommendations/product-recs.html#types-of-data) to operate. The catalog data sync process remains unchanged in a headless implementation, but changes are needed for behavioral data collection.

To integrate Product Recommendations in a headless storefront you must:

1. Send behavioral data to Adobe Sensei to analyze and compute Product Recommendation results. You also can send additional data to enable product recommendation [metrics reporting]({{ site.user_guide_url }}/marketing/recommendation-metrics.html).

1. Fetch product recommendation results and render those results on the page.

You can perform both of these actions using the available SDKs as described in the following workflow.

1. [Install the Product Recommendations]({{ page.baseurl }}/recommendations/install-configure.html) module.

1. Install and use the [Storefront Events SDK]({{ page.baseurl }}/shared-services/storefront-events-sdk.html) to fire the [behavioral events]({{ page.baseurl }}/recommendations/events.html).

    The minimum required events to return Product Recommendations results:

    Event | Category
    --- | ---
    `view` | product
    `add-to-cart` | product
    `place-order` | checkout

    To enable [metrics reporting]({{ site.user_guide_url }}/marketing/recommendation-metrics.html), the following additional events are required:

    Event | Category
    --- | ---
    `impression-render` | recommendation-unit
    `view` | recommendation-unit
    `rec-click` | recommendation-unit
    `rec-add-to-cart-click` | recommendation-unit (if an add to cart button is present in the recommendations template)

1. When the events are fired, use the [Storefront Events Collector]({{ page.baseurl }}/shared-services/storefront-event-collector.html) to handle the events and send them to Adobe Sensei.

1. After the behavioral data is collected, you can [create Product Recommendations]({{ site.user_guide_url }}/marketing/create-new-rec.html) in the Admin.

1. Use the [Recommendations SDK]({{ page.baseurl }}/recommendations/recs-api.html) to fetch the recommendation units on the storefront. The SDK returns necessary product data to render recommendation units on a page.
