# Brainstorming

## Hyperlinks

- https://w3c.github.io/vc-data-model/
- https://w3c.github.io/vc-use-cases/

## URI-addressable Claims
`http://www.journalistblog.com/claim/ebfeb1f712ebc6f1c276e12ec21`
`http://www.journalistblog.com/fact/ebfeb1f712ebc6f1c276e12ec21`
`http://facts.press.org/fact/ebfeb1f712ebc6f1c276e12ec21`

## Hypertext and Verifiable Claims
Coming soon.

## Decentralized Systems and Blogging Platform Plugins
As we consider citizen journalists and bloggers, we can consider blogging platform plugins (e.g. Drupal, Joomla and WordPress plugins) for verifiable factual claims.

### Factual Claims as Custom Post Types
- https://codex.wordpress.org/Post_Types

### Creating, Editing and Revoking Factual Claims
The plugins can include forms for users to create, edit, forward/redirect and revoke factual claims. The plugins can ping lists of services and users whenever factual claims are created, updated or deleted.

### Content Types
The plugins can return content for requests for factual claims’ for the content types of HTML and JSON-LD.

### OpenGraph
The plugins can ensure that the hypertext for factual claims includes OpenGraph data, making factual claims shareable.

### Dependencies
Factual claims can be used or referenced from articles and have dependency relationships with article objects.

The plugins can process blog article creation, editing and deletion events to process dependency graphs across factual claim producers and consumers. Users can automatically subscribe to remote factual claims’ update events as their blog articles depend on remote factual claims. That is, the plugins can also receive subscription requests and subscription cancelation requests to the update and deletion events of factual claims as other users make use of their factual claims.

Journalists can receive notifications about their article dependencies should they update their local factual claims and, should remote factual claims used by journalists update or change, as users of the facts, they also receive notifications promptly. The plugins can email journalists should their articles depend on factual claims which are updated or deleted.

### Embedding Claims in Posts via Shortcodes
One way to embed references to local or remote factual claims into blog articles is using shortcodes:

`[claim id="ebfeb1f712ebc6f1c276e12ec21"]`

`[claim id="http://www.remoteclaim.com/claims/ebfeb1f712ebc6f1c276e12ec21"]`
