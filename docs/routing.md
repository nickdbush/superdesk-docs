---
id: routing
title: Routing
---

When content is published in Superdesk, there are a large variety of workflows available for deciding where it should end up.
There are four important parts to the configuration of the publication pipeline:

- Who gets the content: [subscribers](#subscribers)
- What they should receive: [products](#products)
- Where the content should be sent: destinations
- How the content should be delivered: formats

## Content filters

Content filters define a set of rules for matching against content.
They are built from smaller **filter conditions**, which are simple database queries which check whether an article is a member of the group or not.
There is a wide variety of metadata to match against, such as categories, subject, story HTML, embargo, and so on.

For instance, a content filter with the condition `Subject = Sport` would return the set of all sports articles.

Content filters can optionally be set to **global block** mode.
Content is usually pushed to all subscribers by default – global block turns this into an opt-in operation.
Content that matches this filter is blocked from being sent to subscribers by default, unless deactivated in the subscriber's settings.

An **archive block** prevents matched content from being sent to the archive once it has expired {TODO: Link to expiry docs}.
Instead, it is permanently deleted {TODO: Is the deletion permanent?}.

### Products

Products act as another layer of content filtering in the publication pipeline.
Typical products work exactly the same as a content filter, but can have territorial restrictions and support blocking content.
When saved as a "blocking" product, you can think of it as a filter for all content that does *not* match the filter criteria.
The simplest product has no filters, and therfore includes all published content.

Product codes are comma-separated content descriptors. {TODO: EXPLAIN}

## Subscribers

Subscribers can be thought of as individual customers.
Each subscriber can receive a mixture of products at a number of destinations.
Subscribers can be services such as websites and mobile apps, or other distribution systems such as Superdesk Publisher.

When creating subscribers, you can provide an email to automatically notify when published content is killed (unpublished).
Alternately, add any email address in a valid format in this field.

Keep subscribers organised by setting custom target types (such as for differentiating between newspapers, magazines, businesses, etcetera).
These types are defined in the `subscriber_types` [vocabulary](/vocabulary).

## Internal destinations

While most content will usually be pushed directly to subscribers, Superdesk also has the abilitiy to push content to **internal destinations**.
The content is copied, and then the copy is sent to a selected desk.

Admins can configure the destination desk and stage in the admin settigs {TODO: Link to admin settings}.
Content filters can be used to only move specific content.
Optionally, macros {TODO: Link to macros} can be run on the content to transform it in some way.
These macros can also automatically publish the modified copy from the new desk.

Internal destinations come in very handy for translating content.
For instance, all stories published from the news desk could be automatically copied to a translation desk upon publishing, with a macro that changes the language metadata of the copy.

Alternatively, internal destinations could be used to produce shortened versions of articles that fall within a specific product {TODO: Link to product explanation}.
The first step would be to create a content filter that matches on stories for the product.
Then, content is pushed to a shortening desk, where a macro cuts the story after a certain number of paragraphs, and publishes the content under a new product. {TODO: Cleanup}
