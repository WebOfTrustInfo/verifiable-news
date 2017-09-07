# Brainstorming

## Hyperlinks

- https://w3c.github.io/vc-data-model/
- https://w3c.github.io/vc-use-cases/

## Decentralized Systems and Blogging Platform Plugins

As we think about citizen journalists and bloggers, we can consider blogging platform plugins (e.g. Wordpress and Drupal plugins) for verifiable factual claims.

Such plugins would include a new object type for factual claims and the URI for each factual claim could resemble: 
http://www.journalistblog.com/claims/ebfeb1f712ebc6f1c276e12ec21 or http://www.journalistblog.com/facts/ebfeb1f712ebc6f1c276e12ec21.

The plugins can use the type systems of blogging platforms to interoperate with other systems such as `sitemap.xml` systems. The plugins can return content for requests for factual claims’ for content types HTML and JSON-LD. The plugins can ensure that the factual claims are shareable via OpenGraph data. The plugins can include forms for users to create, edit and revoke factual claims. The plugins can ping lists of services and users whenever factual claims are created, updated or deleted.

Factual claims can be used or referenced from articles and have dependency relationships with article objects. One way to embed references to local or remote factual claims into blog articles is using shortcodes:

`[claim id="ebfeb1f712ebc6f1c276e12ec21"]`

`[claim id="[http://www.remoteclaim.com/claims/ebfeb1f712ebc6f1c276e12ec21"]`

The plugins can process blog article creation, editing and deletion events to process dependency graphs across factual claims providers, users automatically subscribing to remote factual claims’ update events as their blog articles depend on remote factual claims. That is, the plugins can also receive subscription requests and subscription cancelation requests to the update and deletion events of factual claims as other users make use of their factual claims.

Journalists can receive notifications about their article dependencies should they update their local factual claims and, should remote factual claims used by journalists update or change, as users of the facts, they also receive notifications promptly. The plugins can email journalists should their articles depend on factual claims which are updated or deleted.

Considering such plugins, and considering the possible features of such plugins, we can envision website-based and decentralized solutions which include support for citizen journalists and bloggers.
