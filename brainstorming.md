# Brainstorming

## Hyperlinks

- https://w3c.github.io/vc-data-model/
- https://w3c.github.io/vc-use-cases/

## URI-addressable Factual Claims
`http://www.journalistblog.com/claim/ebfeb1f712ebc6f1c276e12ec21`
`http://www.journalistblog.com/fact/ebfeb1f712ebc6f1c276e12ec21`
`http://facts.press.org/fact/ebfeb1f712ebc6f1c276e12ec21`

## Decentralized Systems and Blogging Platform Plugins
As we consider citizen journalists and bloggers, we can consider blogging platform plugins (e.g. Drupal, Joomla and WordPress plugins) for verifiable factual claims.

### Factual Claims as Custom Post Types
https://codex.wordpress.org/Post_Types#Custom_Post_Types

### Creating, Editing and Revoking Factual Claims
The plugins can include forms for users to create, edit, move/forward/redirect and delete/revoke factual claims. The plugins can ping lists of services and users whenever factual claims are created, updated or deleted.

### Factual Claims and Content Types
The plugins can return content for requests for factual claims for the content types of HTML and JSON-LD.

### Factual Claims and Schema.org Schemas
The plugins can embed verifiable claim schema into hypertext outputs using RDFa or as JSON-LD through the `<script>` element.

### Factual Claims and OpenGraph
The plugins can ensure that the hypertext for factual claims includes OpenGraph data, making factual claims shareable.

### Embedding References to Factual Claims in Posts via Shortcodes
One way to embed references to local or remote factual claims into blog posts is using shortcodes. The plugins can process the creation, editing and deletion of blog posts to process dependencies on local and remote factual claims. 

`[claim id="ebfeb1f712ebc6f1c276e12ec21"]`

`[claim id="http://www.remoteclaim.com/claims/ebfeb1f712ebc6f1c276e12ec21"]`

### Modifying the Webpages for the Authoring of Posts
Another way to attach posts and claims is to add form elements on the post-authoring webpages to attach and detach local and remote claims.

### Dependency Relationships
Factual claims can be used or referenced from posts and have dependency relationships with post objects. News articles depend on other articles and, pertinent to this discussion, news articles depend on facts.

The plugins can receive subscription requests and subscription cancelation requests to the events of factual claims as other users make use of factual claims as remote factual claims.

Journalists can receive notifications about post dependencies should they update their local factual claims and, should remote factual claims used by journalists update or change, as users of the facts, they also receive notifications. The plugins can email journalists should their posts depend on factual claims which are updated or deleted.
