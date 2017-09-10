# Bots, Fake News, and Verifiable Claims

Summary of Credentials CG Telecon discussing these topics on 2017-08-15.

[Full transcript and audio](https://w3c-ccg.github.io/meetings/2017-08-15/#topic-2)

## About

Moses Ma led a Credentials Community Group discussion about Bots, Fake News, and Verifiable Claims. We had attendees from the Verifiable Claims community and news technologists (attendee list is at the end). Despite the limited time allocated, we derived a number of useful insights and developed a plan for engagement with the journalistic community for next steps. This is a summary of our findings.

## Intro

Many in and beyond the Verifiable Claims community have suggested Verifiable Claims are conceptually well-suited to addressing problems of fake news. However, we need input from working journalists to understand what tools we can provide to fit into their workflow, and more broadly, what would they like to express.

## What would it look like to use Verifiable Claims to address fake news? 

At a very high level, a set of Verifiable Claims would be a basis from which the credibility of individual statements can be deduced. This might be in the form of positive or negative claims.

A positive claim might be along the lines of attributions of quotes or facts to sources. 

Negative claims are trickier, because the author of the claim being disputed has no incentive to reveal these claims. Because of this, negative claims are most likely to be useful when they can be viewed as the result of the cumulative efforts of many different news sites vetting articles.

Realistically in journalism, it's unlikely that formal reasoning can be applied to state a claim is false. So rather than a claim of the form "this article says X and X is false", it's more likely that a claim stating "this article says X and that's a misleading claim" (with references to sources)" would be useful.

## Who are the interested parties in the system and how would they use claims?

Significant parties include:

- Journalists
- fact-checkers/reviewers
- news consumers

Journalists would most likely want to create Verifiable Claims containing positive assertions about who said what. Significantly, this is part of good journalism (citing, tracing) anyway. For this reason, Verifiable Claims could be used in the journalist's toolset to help bake good journalism into web in a verifiable way. 

Fact-checkers or reviewers could create positive or negative claims, and these tend to be more interesting in the aggregate.

News consumers want to know if what they are reading contains misleading claims. A good analogy is a browser displaying warnings against scam sites or expired SSL certs; perhaps browser plugins could help flag articles with misleading claims. The reader could be informed that reviewers x, y, and z determined this article to be in accurate, with pointers to further references.

Other candidate models for news consumers include:
- Snopes: here are claims signed by X, Y
- Wikipedia footnotes: Footnotes lead to signed claims of facts

## Focus on fact-checking rather than rating sites

In our discussion, there was broad consensus that it is more promising to focus on fact-checking rather than rating sites, for the following reasons:

Realistically, even sites believed to contain many misleading stories do contain fact-based stories as well. 
Making a claim at the site level is more likely to land the claimant in legal trouble
Readers may self-partition themselves by picking claimants they trust, which may just prolong segmentation

## Is it useful to identifying journalists/reviewers as sources of credible claims?

There was consensus that identification of the sources of information (where possible) was useful, but mostly as a means to distinguish professional journalists from casual bloggers.

Similarly, knowing that a story has been vetted by a professional is useful.

These could be derived from Verifiable Claims of the form:
- This journalist works for news organization X and has published articles {y1..yn}
- This story has been vetted by a professional employed by Z

### Why broader statements are unlikely to be useful

This information is more useful than attempting broader statements; e.g. a system of credentialing "credible" journalists would likely not succeed (and is very subjective).

Furthermore, in reputation systems, it's hard to cryptographically know a negative reputation exists, because the person with bad reputation has no incentive to disclose. Hard to know this information will flow to the user.

### How does identity of journalists/reviewers related to credibility of content

Author and reviewer identity are just small inputs into whether an article as a whole can be considered credible. What's more interesting is the cumulative effect of many different news sites vetting articles. So at scale, flagging content as credible / not credible becomes more about consensus and less about identity.

## So who can a news consumer trust?

In the model of a browser plugin flagging misleading content, we glossed over the question of how sources are selected. One possibility is that the person browsing can choose their own sources of truth (or claims) they want to listen to. Obviously, this selection could be biased based on existing preferences. Again, this is why aggregation of claims is more likely to be helpful; that is, assuming the sources of claims are not artificially magnified, e.g. through use of bots.

## Identifying people vs bots

Why is this important? Likes, sharing, etc are providing a megaphone for things that otherwise not have an audience. 

So is it possible to identify a bot? There are two ways we discussed. One is activity based; i.e. a bot can retweet things much faster than a human. But such a system would need to factor in false positive.

What sounds more promising is focusing on a network of people making attestations. For example, other people can make the claim about you are a human in some form. To do this, we would need to bring in richness of real world, e.g. possession of a bank account. (E.g. without disclosing what the bank is). Bots can't say these and/or it becomes prohibitively expensive.

In general, the goal would be to find actions/claims that are economically feasible for humans but infeasible for bots. Even if we can't make the system completely secure, we can raise the cost of defrauding the system. 

One area we considered is if we had a trusted issuer. If so, this question would be easy to solve, e.g. if the UK gov could do this. Getting a trusted issuer is a difficult problem, especially given the current state of government technology. Maybe banks because of KYC, but not everyone has a bank account. 

## Next steps	

As a community, we'll fail if we don't have journalists engaged. We must get journalists engaged to understand what they want to do, or if any existing models (e.g. Wikipedia footnotes) are preferred.

The Verifiable Claims community wants to know which tools we can provide that would make you more successful. Anything without input from news organizations is a wild guess.

Helpfully, journalists are inherently skeptical, so their involvement in designing a solution will help ensure success of a Verifiable Claims-based system in combating fake news.

## Attendees
Dave Longley, Evan Sandhaus, Ryan Grant, Claire Rumore, Mike Lodder, Moses Ma, Manu Sporny, David Chadwick, Lionel Wolberger, Kim Hamilton Duffy, Adam Migus, Matt Stone, Nathan George, Joe Andrieu, Adam Sobieski, Adam Lake, Drummond Reed, Dan Burnett, Chris Webber
