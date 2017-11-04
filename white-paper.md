# Verifiable News: A White Paper

## Executive Summary

In 2017, our global media landscape finds itself in a precarious situation: trust in media is at an all time low, and decentralized production and centralized, algorithmic distribution have created a perfect storm for the rise of misinformation, disinformation and the scourge generally referred to as fake news. This is not a partisan problem but rather one that is driving polarization while simultaneously undermining public trust in institutions.

This white paper seeks to address these challenges and to produce solutions. This white paper seeks to propose policy, standards, and technologies to help curb inauthentic agents (bots), to mitigate the spread of online misinformation and to defend society from both wholesale and targetable online disinformation campaigns and manipulation.

## Setting

Research shows that the number of people around the world frequently using online sources to follow news is growing fast, by various measures. As digital media is increasingly becoming an essential source of news for many, we have also observed a rise in the quantity and complexity of misinformation and disinformation being shared on the platforms many are using to access and follow news, such as Facebook, Twitter, YouTube, WhatsApp, SnapChat.

Fake news, hoaxes, false rumors, mis-contextualized content and targeted disinformation are having real, measurable, offline effects. Disinformation has impacted the UK’s decision to leave the EU, the refugee crisis in Europe, and the 2016 US presidential election.

In Eastern Europe, the Middle East, East and South-East Asia, and Latin America, state actors have flooded online networks with propaganda and sockpuppet armies to stifle dissent, smear journalists, and manipulate public opinion [1]. The misinformation threat to Western Europe and the US has only more recently received the attention that it deserves.

These challenges, though, have been exacerbated by the increasingly algorithmic nature of content distribution on social networks. When, in September 2016 Facebook removed human editors from its Trending process, the algorithmic replacement almost immediately started surfacing rumors, conspiracy theories and misinformation. In October 2017, the New York Times reported on Google's AdSense advertising network pushing false headlines and rumors onto the homepages of prominent fact-checking sites Snopes and PolitiFact.

The Internet’s current capacity to support democratic societies in making well-informed decisions is being subverted by globally networked actors, and, with every large, breaking news event, we see more evidence of trending misinformation, much of it being repurposed and distributed through international networks.

Newsrooms need new ways to deal with the misinformation ecosystem which also address the underlying issues of trust and sustainability. They can’t tackle the problem alone. Platforms such as Google, Facebook, YouTube and Twitter are central in the distribution of news, and have come under fire for amplifying misinformation and fake news.

Automating the detection of misinformation is not always straightforward; human inputs are still invaluable in the process. At present, newsrooms’ abilities to present structured data pertaining to credibility in a way that can be ingested by platforms and, in turn, drive traffic, is very limited. The urgency of addressing these challenges should not be underestimated. Left unchecked, the erosion of public trust in media will further undermine a fundamental pillar of democracy.

Following the investigative reporting by Silverman, et al, the platforms have begun to acknowledge their roles in addressing online misinformation and its spread. Notably, Facebook has partnered with the IFCN and other fact-checking organizations in an effort to bring third-party reviews to disputed content [2]. They have additionally begun to surface news article contextual information, and to limit the ability for fake news webpages to monetize that content. Google has also looked to third-party fact-checking organizations to help them with a human layer to support their efforts; they now surface fact-checks into their search results and Google News results which trigger on keyword or key phrase searches.

Google has supported work with the Duke Reporters Labs to create a fact-checking schema called ClaimReview for Schema.org. A new schema for news organizations is pending. Varieties of article schemas are versioning to include: advertiser content and satirical articles. Schemas for news articles are versioning to include varieties: analysis, background, opinion, reportage and review.

## W3C and the Credibility Coalition
A strength of our approach is its reach and diversity across a diverse, global set of media partners, research institutions, technology companies, and international standards bodies. Toward further innovation and solutions, we can look to the W3C Credentials Community Group and to the W3C Credibility Community Group.

Starting in 2013, the W3C Credentials Community Group started work on solutions for trust assertions, followed shortly thereafter by the Rebooting Web of Trust Community and W3C Verifiable Claims Working Group. These groups, composed of 150+ individuals and organizations, are currently focused on the creation, storage, transmission, and verification of digital credentials via the Internet.

Starting in 2017, the W3C Credibility Community Group (CCG) is working to establish Web-wide standards and technologies to take in machine and human generated credibility indicators for claims, sources, images, videos, and webpages, from both first- and third-party agents. The CCG is the W3C expression of the work of the Credibility Coalition, a group led by Meedan and Hacks/Hackers, that works with foundation funding to: develop an initial specification for these indicators; build broad consensus around these indicators; pilot initial data markup efforts using the draft schema; pilot social science research on UI (user interface) and UX (user experience) expressions of dispute indicators in situ; and, to carry forward a process that engages a broader community of stakeholders around this work to fundamentally address misinformation and disinformation on the open Web.   

## Assessing the Veracity of Information
Assessing the veracity of information is a starting point for mitigating the spread of online misinformation. For the purposes of this white paper we will consider the varying structures and challenges for assessments made at the claim, source, and article level.  Historically, the journalistic practice of verification and fact-checking fell to a member of the copy editing team called the fact-checker. They would assess an article for any provable assertions (dates, event names, event sequencing, quotations, person names, statistics, etc.) and check reference sources (databases, reporter’s notes, transcripts, CIA factbooks, etc) and confirm or correct these assertions. The process and references in this first-party ante-hoc fact-checking generally go unseen to the end user. Post-hoc first-party fact-checking comes through the public editor and is presented in errata or corrections section of a publication. As media production has become highly decentralized and the presence of misinformation and disinformation in our social newsfeeds has become a global pre-occupation, we have seen a rise of third-party post-hoc fact checking initiatives. 

With this response, comes the need to expose the processes and referents used to arrive at a conclusion and to standardize the vocabulary we use to classify a wide range of human- and machine-generated credibility indicators as they relate to individual assertions, articles, and sources.  

We will touch briefly on the challenge of article-level veracity assessments. The challenge of article classification precedes and determines appropriate processes and vocabularies when making  article-level assessments. Satire and humor tags and descriptors, however, are often used by hyper-partisan or agenda-driven content as a means of deflecting scrutiny or avoiding automated flagging.

The vocabularies we use to classify content are much-debated and, as Caroline Jack states in her report, Lexicon of Lies, for Data & Society, “(t)he words we choose to describe media manipulation can lead to assumptions about how information spreads, who spreads it, and who receives it. These assumptions can shape what kinds of interventions or solutions seem desirable, appropriate, or even possible [3].” The best classification work has been done by Claire Wardle for First Draft, their schema includes: satire or parody; false connection; misleading content; false context; imposter content; manipulated content; and, fabricated content.  Claire and Hossein Derakhshan have just released a report, INFORMATION DISORDER: Toward an interdisciplinary framework for research and policy making, that extends that schema, looking at the separate roles and motivations of the creators, producers, and interpreters/re-distributors of this content [5].

## Assessing the Credibility of Information Sources
Assessing the credibility of information sources is an effective strategy for mitigating the spread of online misinformation primarily because it can be used as a broad filter and does not rely on claim or article-level assessments. Source-level credibility assessments can be built from source-attributed articles and the claims contained therein, and can also be created from machine analysis of publishing behaviors, including sharing patterns, and plagiarism.

There are several efforts underway to classify junk news sources, including the PBS Newstracker and Veracity.AI. Both efforts apply classify junk news sources based on machine learning trained against known junk news providers.  Among the factors they assess when scoring source credibility: clickbait headline; anonymous byline; false content; misleading content; inaccurate context; plagiarism; low quality ads; partisan rhetoric; inflammatory tone; hate speech; young domain; and multi-site publishing.

## How Could Verifiable Claims be Used?
At a very high level, a set of Verifiable Claims would be a basis from which the credibility of individual statements can be deduced. This might be in the form of positive or negative claims.

A positive claim might be along the lines of attributions of quotes or facts to sources. A negative claim might dispute that an article accurately represents the source referred to or accurately reports a statistic or dataset. A negative claim can also arise from a logical fallacy or mis-contextualization of a fact. 

Verifiable Claims are conceptually well-suited to addressing problems of fake news, but collaboration requires input from working journalists to understand what tools we can provide to fit into their workflow, and more broadly, what would they like to express.

Parties involved in a Verifiable News ecosystem can include:

- journalists
- fact-checkers/reviewers
- news consumers

Journalists would most likely want to create Verifiable Claims containing positive assertions about who said what. Significantly, this is part of good journalism (citing, tracing) anyway. For this reason, Verifiable Claims could be used in the journalist’s toolset to help bake good journalism into web in a verifiable way. Fact-checkers or third-party reviewers could dispute identified claims and/or create positive or negative claims in an article. These third party signals could be aggregated and analyzed and/or represented in the aggregate.

News consumers want to know if what they are reading contains misleading claims, and want to know on whose authority a claim is labeled as verified or disputed. A good analogy is a browser displaying warnings against scam sites or expired SSL certs; perhaps browser plugins could help flag articles with misleading claims. The reader could be informed that reviewers x, y, and z determined this article to be in accurate, with pointers to further references.

## The Role of Identity
Identification of the sources of news or sources (where possible) is considered beneficial, not from the perspective of establishing credibility, but as a means to distinguish professional journalists from casual bloggers or bots. In some cases, the identity of the quoted source or author/journalist is material to the veracity of a claim they are making, in these cases having a means of confirming or denying the veracity of a claimed identity can be sufficient to verify or debunk a claim. Similarly, knowing that a story has been vetted by a professional news reporter is useful.

These could be derived from Verifiable Claims of the form:

- this journalist works for news organization X and has published articles {y1..yn}
- this story has been vetted by a professional employed by Z

Decentralized Identifiers offer a decentralized approach for cryptographically strong, but usable identity management, making it more difficult to spoof attribution.

Author and reviewer identity are just small inputs into whether an article as a whole can be considered credible. What’s more interesting is the cumulative effect of many different news sites vetting articles. So at scale, flagging content as credible / not credible becomes more about consensus and less about identity. And, seeing geographic, ideological, or even linguistic boundaries to this consensus can indicate when a claim has a political or social intent.

## Account Verification
Digital wallets and identifying credentials, presently being worked on by the W3C Credentials Community Group, are effective means of enhancing account verification processes. Enhancing account verification processes is expected to curb fake accounts, sockpuppetry, social bots and cyborgs across the Web. Curbing social bots is an effective strategy for mitigating the spread of online misinformation.

“We find evidence that social bots play a key role in the spread of fake news. Accounts that actively spread misinformation are significantly more likely to be bots. Automated accounts are particularly active in the early spreading phases of viral claims, and tend to target influential users. Humans are vulnerable to this manipulation, retweeting bots who post false news. Successful sources of false and biased claims are heavily supported by social bots. These results suggests that curbing social bots may be an effective strategy for mitigating the spread of online misinformation” [4].

## Conclusion
The current Internet media landscape has proven a hospitable domain for those choose to weaponize mis- and disinformation in service of political and corporate agendas. We have arrived at the point Wardle and Derahkshan identify as widespread digital Information Disorder in which the assumed role of journalism to assert and defend a common set of publicly accepted facts to ground meaningful public debate and policy has been compromised. We must recognize that the very forces that have created this setting - the advance of AIs, the decentralization of modes of producing, publishing, re-sharing, and the platforms’ algorithmic approaches to sorting information - will only evolve to better predict human behavior, and, in the case of AIs, to better resemble legitimate human actors. 

One productive area of response is to standardize the way we signal disputes and the evidence we provide in support of those signals. The work of digital identity and digital credentialing combined with a robust effort to expand the existing annotation standard to accept a vocabulary specific to disputes, fact-checks, and verification is, perhaps, the most productive response we can take at this point in time to a challenge which will will evolve and persist.

## References
[1] Bradshaw, Samantha, and Philip N. Howard. “Troops, trolls and troublemakers: A global inventory of organized social media manipulation.”

[2] International Fact-Checking Network. https://www.poynter.org/channels/fact-checking

[3] Jack, Caroline. Lexicon of Lies, Data & Society. https://datasociety.net/pubs/oh/DataAndSociety_LexiconofLies.pdf 

[4] Shao, Chengcheng, Giovanni Luca Ciampaglia, Onur Varol, Alessandro Flammini, and Filippo Menczer. “The spread of fake news by social bots.” arXiv preprint arXiv:1707.07592 (2017).

[5] Wardle, Claire and Hossein Derakhshan. INFORMATION DISORDER: Toward an interdisciplinary framework for research and policy making.
