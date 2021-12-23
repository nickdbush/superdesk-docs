---
id: vocabulary
title: Vocabularies
---

Superdesk is an incredibly flexible CMS and, as such, is highly configurable.
The bulk of this configuration is done through the admin UI, or through Superdesk's controlled vocabulary.
You can think of the controlled vocabulary as lists of fields and values that are used throughout Superdesk.

For instance, the `subscriber_types` vocabulary defines the types of subscribers available, and the formats they should receive content in.
In the `.../server/data/vocabularies.json` file, an example subscriber is defined as so:

```json
{
  "is_active": true,
  "name": "All",
  "qcode": "all",
  "formats": [
    { "name": "NTBNITF", "qcode": "ntbnitf" },
    { "name": "NINJS", "qcode": "ninjs" },
    { "name": "AAP NewsML 1.2", "qcode": "newsml12" },
    { "name": "NewsML G2", "qcode": "newsmlg2" }
  ]
}
``` 