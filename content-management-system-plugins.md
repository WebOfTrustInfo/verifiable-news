# Content Management System Plugins

## URI-addressable Factual Statements
`https://www.journalistblog.com/facts/ebfeb1f712ebc6f1/`

`https://facts.press.org/facts/ebfeb1f712ebc6f1/`

## Decentralized Systems and Content Management System Plugins
We can consider content management system (e.g. [Drupal](http://www.drupal.com/), [Joomla](https://www.joomla.com/) and [WordPress](https://wordpress.org/)) plugins for decentralized systems of verifiable factual statements.

### Factual Statements as Custom Post Types
Factual statements can be implemented as a [custom post type](https://codex.wordpress.org/Post_Types#Custom_Post_Types).

`https://www.journalistblog.com/facts/ebfeb1f712ebc6f1/`

### Creating, Editing and Revoking Factual Statements
Plugins can provide forms and API for users to create, edit, move/forward/redirect and delete/revoke factual statements. Plugins can ping lists of services and users whenever factual statements are created, updated or deleted (e.g. using [XML-RPC](https://codex.wordpress.org/XML-RPC_Extending)).

### Factual Statements and Content Types
Plugins can return content for requests for factual statements for content types including HTML (`text/html`, `application/xhtml+xml`) and JSON-LD (`application/ld+json`).

### Factual Statements and Schema.org Schemas
Plugins can embed factual statement schema into hypertext using RDFa and/or as JSON-LD through the `<script>` element.

### Factual Statements and OpenGraph
Plugins can ensure that the hypertext for factual statements includes [OpenGraph](http://ogp.me) data, enhancing the shareability of factual statements on social media.

### Embedding References to Factual Statements in Posts via Shortcodes
One way to attach posts and local or remote factual statements is to embed references to factual statements into blog posts using [shortcodes](https://codex.wordpress.org/Shortcode_API). Plugins can process the creation, editing and deletion of blog posts to process posts' dependencies on local and remote factual statements.

`[statement id="ebfeb1f712ebc6f1"]`

`[statement id="https://www.remote.com/facts/ebfeb1f712ebc6f1/"]`

### Modifying the Webpages for the Authoring of Posts
Another way to attach posts and local or remote factual statements is to add form elements on post-authoring webpages to modify post metadata, attaching and detaching posts and local and remote statements.

### Dependency Relationships
News articles depend on other articles and, pertinent to this discussion, news articles depend on facts.

Plugins can receive subscription requests and subscription cancelation requests with regard to the events of factual statements. Should local or remote factual statements used by journalists update or change, the journalists receive notifications. Plugins can email or message journalists should their news articles depend on factual statements which change.

### Indexing Metadata
Plugins can output post metadata into posts' hypertext, invisibly to readers but visibly to search engines, so that search engines indexing posts and factual statements for search and retrieval can see how specific posts and factual statements relate.

## Services and Supernodes

### Creating, Editing and Revoking Factual Statements

Services can receive pings when distributed factual statements are created, edited or deleted (e.g. using [XML-RPC](https://codex.wordpress.org/XML-RPC_Extending)). Services can ping lists of other services and users whenever factual statements are created, updated or deleted (e.g. using [XML-RPC](https://codex.wordpress.org/XML-RPC_Extending)).

### Searching Factual Statements
Services can provide search services over aggregated collections of factual statements.

### Detecting Identical and Similar Factual Statements
Services can detect identical and similar natural language factual statements from different users. Services can merge identical and paraphrased factual statements from different users.

### News Articles Utilizing and Corroborating Factual Statements
Services can provide lists of distributed posts and news articles which utilize factual statements. Services can provide lists of distributed posts and news articles which corroborate factual statements.

### Indexing Metadata
Plugins can output factual statement metadata into statements' hypertext, invisibly to readers but visibly to search engines, so that search engines indexing posts and factual statements for search and retrieval can see how specific posts and factual statements relate.

### Trending or Popular Factual Statements
Services can indicate which factual statements are trending or popular in terms of journalistic usage or in terms of sharing on social media, for example for fact-checking organizations.

### Fact-checking Factual Statements
Services can convenience fact-checking organizations.

### Hosting or Hosting Copies of Factual Statements
Plugins can provide forms and API for users to create, edit and delete/revoke factual statements hosted or co-hosted by services.

`https://facts.press.org/facts/ebfeb1f712ebc6f1/`

### Discussing Factual Statements
Services can provide areas for comments and discussions.

### Aggregating Factual Statements into Threads, Stories or Narratives
Services can aggregate factual statements into threads, stories or narratives.

### Exporting Collections of Factual Statements into Machine-utilizable Formats
Services can export collections of factual statements into machine-utilizable formats.

## Other Producers and Consumers of Factual Statements

Individuals and organizations other than journalistic can produce and consume factual statements. Companies, non-profits, universities, laboratories and public-sector organizations, for example, can produce and consume factual statements.
