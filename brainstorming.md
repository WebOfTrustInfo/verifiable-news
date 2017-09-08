# Brainstorming

## Hyperlinks

- https://w3c.github.io/vc-data-model/
- https://w3c.github.io/vc-use-cases/

## URI-addressable Factual Claims
`http://www.journalistblog.com/fact/ebfeb1f712ebc6f1c276e12ec21`

`http://facts.press.org/fact/ebfeb1f712ebc6f1c276e12ec21`

## Decentralized Systems and Blogging Platform Plugins
We can consider blogging platform plugins (e.g. Drupal, Joomla and WordPress plugins) for verifiable factual claims.

### Factual Claims as Custom Post Types
https://codex.wordpress.org/Post_Types#Custom_Post_Types

### Creating, Editing and Revoking Factual Claims
The plugins can include forms and API for users to create, edit, move/forward/redirect and delete/revoke factual claims. The plugins can ping lists of services and users whenever factual claims are created, updated or deleted.

### Factual Claims and Content Types
The plugins can return content for requests for factual claims for the content types of HTML and JSON-LD.

### Factual Claims and Schema.org Schemas
The plugins can embed verifiable claim schema into hypertext outputs using RDFa and/or as JSON-LD through the `<script>` element.

### Factual Claims and OpenGraph
The plugins can ensure that the hypertext for factual claims includes OpenGraph data, making factual claims shareable.

### Embedding References to Factual Claims in Posts via Shortcodes
One way to attach posts and local or remote factual claims is to embed references to factual claims into blog posts using shortcodes. The plugins can process the creation, editing and deletion of blog posts to process posts' dependencies on local and remote factual claims. 

`[claim id="ebfeb1f712ebc6f1c276e12ec21"]`

`[claim id="http://www.remoteclaim.com/claim/ebfeb1f712ebc6f1c276e12ec21"]`

### Modifying the Webpages for the Authoring of Posts
Another way to attach posts and local or remote factual claims is to add form elements on post-authoring webpages to modify post metadata, attaching and detaching posts and local and remote claims.

### Dependency Relationships
Factual claims can be used or referenced from posts. News articles depend on other articles and, pertinent to this discussion, news articles depend on facts.

The plugins can receive subscription requests and subscription cancelation requests to the events of factual claims as other users make use of factual claims as remote factual claims.

Journalists can receive notifications about post/claim dependencies as they update their local factual claims and, should remote factual claims used by journalists update or change, as users of the factual claims, they also receive notifications. The plugins can email journalists should their posts depend on factual claims which change.

## Factual Claims Services and Supernodes

### Hosting Factual Claims
The blogging platform plugins can include forms and API for users to create, edit and delete/revoke factual claims at remote locations. Factual claims services can host factual claims and receive pings when distributed claims are created. Factual claims services can ping lists of services and users whenever factual claims are created, updated or deleted.

`http://facts.press.org/fact/ebfeb1f712ebc6f1c276e12ec21`

### Factual Claims and Search
Factual claims services can provide search services over collections of aggregated factual claims. 

### Detecting Identical and Similar Factual Claims
Factual claims services can detect identical and similar factual claims from different users.

### Factual Claims and Lists of News Articles Utilizing and Corroborating Them
Factual claims services can list distributed posts and news articles utilizing and corroborating factual claims.
