# Brainstorming

## URI-addressable Factual Claims
`https://www.journalistblog.com/facts/ebfeb1f712ebc6f1c276e12ec21`

`https://facts.press.org/facts/ebfeb1f712ebc6f1c276e12ec21`

## Decentralized Systems and Blogging Platform Plugins
We can consider blogging platform plugins (e.g. [Drupal](http://www.drupal.com/), [Joomla](https://www.joomla.com/) and [WordPress](https://wordpress.org/) plugins) for verifiable factual claims.

### Factual Claims as Custom Post Types
Factual claims can be implemented as a [custom post type](https://codex.wordpress.org/Post_Types#Custom_Post_Types).

`https://www.journalistblog.com/facts/ebfeb1f712ebc6f1c276e12ec21`

### Creating, Editing and Revoking Factual Claims
Plugins can provide forms and API for users to create, edit, move/forward/redirect and delete/revoke factual claims. Plugins can ping lists of services and users whenever factual claims are created, updated or deleted (e.g. using [XML-RPC](https://codex.wordpress.org/XML-RPC_Extending)).

### Factual Claims and Content Types
Plugins can return content for requests for factual claims for content types including HTML (`text/html`, `application/xhtml+xml`) and JSON-LD (`application/ld+json`).

### Factual Claims and Schema.org Schemas
Plugins can embed factual claim schema into hypertext using RDFa and/or as JSON-LD through the `<script>` element.

### Factual Claims and OpenGraph
Plugins can ensure that the hypertext for factual claims includes [OpenGraph](http://ogp.me) data, enhancing the shareability of factual claims on social media.

### Embedding References to Factual Claims in Posts via Shortcodes
One way to attach posts and local or remote factual claims is to embed references to factual claims into blog posts using [shortcodes](https://codex.wordpress.org/Shortcode_API). Plugins can process the creation, editing and deletion of blog posts to process posts' dependencies on local and remote factual claims. 

`[claim id="ebfeb1f712ebc6f1c276e12ec21"]`

`[claim id="https://www.remote.com/facts/ebfeb1f712ebc6f1c276e12ec21"]`

### Modifying the Webpages for the Authoring of Posts
Another way to attach posts and local or remote factual claims is to add form elements on post-authoring webpages to modify post metadata, attaching and detaching posts and local and remote claims.

### Dependency Relationships
News articles depend on other articles and, pertinent to this discussion, news articles depend on facts.

Plugins can receive subscription requests and subscription cancelation requests to the events of factual claims. Should local or remote factual claims used by journalists update or change, the journalists receive notifications. Plugins can email or message journalists should their news articles depend on factual claims which change.

#### Indexing Post Metadata
Plugins can output post metadata into posts, invisibly to readers but visibly to search engines, so that search engines indexing posts and factual claims for search and retrieval can see how specific posts and factual claims relate.

## Factual Claims Services and Supernodes

### Creating, Editing and Revoking Factual Claims

Factual claims services can receive pings when distributed factual claims are created, edited or deleted (e.g. using [XML-RPC](https://codex.wordpress.org/XML-RPC_Extending)). Factual claims services can ping lists of other services and users whenever factual claims are created, updated or deleted (e.g. using [XML-RPC](https://codex.wordpress.org/XML-RPC_Extending)).

### Searching Factual Claims
Factual claims services can provide search services over aggregated collections of factual claims. 

### Detecting Identical and Similar Factual Claims
Factual claims services can detect identical and similar factual claims from different users. Factual claims services can merge identical and paraphrased factual claims from different users.

### News Articles Utilizing and Corroborating Factual Claims
Factual claims services can provide lists of distributed posts and news articles which utilize factual claims. Factual claims services can provide lists of distributed posts and news articles which corroborate factual claims.

### Trending or Popular Factual Claims
Factual claims services can indicate which factual claims are trending or popular in terms of journalistic usage or in terms of sharing on social media, for example for fact-checking organizations.

### Hosting or Hosting Copies of Factual Claims
Plugins can provide forms and API for users to create, edit and delete/revoke factual claims hosted or co-hosted by factual claims services.

`https://facts.press.org/facts/ebfeb1f712ebc6f1c276e12ec21`

### Aggregating Factual Claims into Threads, Stories or Narratives
Factual claims services can aggregate factual claims into threads, stories or narratives.

### Exporting Collections of Factual Claims into Machine-utilizable Formats
Factual claims services can export collections of factual claims into machine-utilizable formats.
