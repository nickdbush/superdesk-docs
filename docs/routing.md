---
id: routing
title: Routing
---

When content is published in Superdesk, there are a large variety of workflows available for deciding where it should end up.

https://sofab.atlassian.net/wiki/spaces/SDHOWTO/pages/5011538016/Publishing+Distribution

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

## Internal destinations

While most content will usually be pushed directly to subscribers, Superdesk also has the abilitiy to push content to **internal destinations**.
The content is copied, and then the copy is sent to a selected desk.

Admins can configure the exact desk and stage in the admin settigs {TODO: Link to admin settings}.
Optionally, macros {TODO: Link to macros} can be run on the content to transform it in some way.
These macros can also automatically publish the modified copy from the new desk.

{TODO: Discuss content filters}

Internal destinations come in very handy for translating content.
For instance, all stories published from the news desk could be automatically copied to a translation desk upon publishing, with a macro that changes the language metadata of the copy.

Alternatively, internal destinations could be used to produce shortened versions of articles that fall within a specific product {TODO: Link to product explanation}.
The first step would be to create a content filter that matches on stories for the product.
Then, content is pushed to a shortening desk, where a macro cuts the story after a certain number of paragraphs, and publishes the content under a new product. {TODO: Cleanup}
