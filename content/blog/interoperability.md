---
title: "Interoperability"
date: 2025-09-12T14:01:46-04:00
draft: false
katex: false
mermaid: false
description: A Modern Successor to Antitrust Law
---

A few months ago my Android phone was stolen, so I decided that it was finally time for me to conform and buy an iPhone. And I have to say, I am shocked at how you all have been living. iOS apps are full of bugs and limitations that you iCels don't seem to realize are totally avoidable[1]. Apple has leveraged peer pressure to bully us into choosing an inferior mobile ecosystem. They have no incentive to improve the quality of their software because their walled garden is enough to keep us in, and as a result we get a much worse experience than we should.

<!-- We currently have an epidemic of companies engaging in anticompetitive practices that hurt consumers while benefiting no one but themselves. The main culprit is Apple, who has leveraged peer pressure to bully users into choosing an inferior mobile ecosystem full of limitations and bugs. They have no incentive to improve the quality of their software because their walled garden is enough to keep users in, and as a result we get a much worse experience than we should. -->

Apple is engaging in anticompetitive practices that benefit no one but themselves. These practices are legal, but they shouldn't be. Another example of an anticompetitive practice which benefits no one but the company doing it is buying up your competitors to form a monopoly. We made that practice illegal, and we should do the same thing with intentional incompatibility. We need a modern successor to pick up where antitrust law left off. The EU has introduced several regulations with this intent, but they seem to have missed the mark and introduced convoluted, highly specific limitations that will not generalize well. I would like to propose an _**interoperability law**_ that should solve this problem, and that I hope is well-reasoned enough to _only_ target anticompetitive practices which have no benefit to consumers. Here is roughly what the law would say:

> Define _interoperability_ to be when one of a company's products can be substituted for an alternative without affecting the regular functioning of their other products[2].
> 1) Companies may not make any form of interoperability impossible.
> 2) Companies may not make any decision with the sole purpose or effect of making interoperability harder.
> 3) This law supercedes any intellectual property laws that it may conflict with.

Note that the third parties creating compatible products would still need to do lots of reverse engineering. The law only requires that companies make compatibility _possible_, not that they enable it by providing documentation, etc.

Here are some example consequences of the law:
- Printer companies would have to allow third parties to sell compatible ink cartridges.
- Apple would have to allow Android apps to use their iMessage protocol. This includes iOS users seeing blue bubbles when they message a compatible Android.
- Instead of requiring Apple to sell phones with USBC ports, this would allow other companies to sell phones with lightning ports.
- Social media companies would have to allow alternative frontends.

Of these consequences, the last one has the greatest potential to completely disrupt an industry, as an alternative social media frontend could simply choose to not display ads. However, I think this would not destroy the social media industry, and in fact it could make social media less problematic.

Many users would continue using the default frontend, but there are a few things that social media companies could do to mitigate the problem of ad-blocking frontends:

- They could stop labeling sponsored content, so that the frontend can't tell the difference between ads and normal content
  - Frontends could respond by applying their own algorithm to filter out content that they think is an ad. But more generally they could apply their own algorithm to select the content that they think the user will be the most interested in, likely improving on in-house algorithms. This is a good idea for more reasons than just filtering out ads, and is already a benefit of this law.
- They could put a delay between sending the ad to the user and sending more content to the user, so now the choice is between watching the ad or staring at a blank screen for 5 seconds.
- They could start showing us ads that we _want_ to see.

Ads that we want to see? Isn't that an oxymoron? I don't think it is. Or at least, in theory it doesn't have to be. The ultimate goal of advertising is to increase sales, and when a user chooses to buy something it is generally because the transaction is mutually beneficial. So if the industry started optimizing for sales directly instead of indirectly through impressions, then in theory there would be no reason to show users ads that they are not genuinely interested in. This would have the additional side effect of taking away the incentive for social media companies to keep you scrolling your life away, since commissions are not directly proportional to session length the way that impressions are.

## A Variant

Alternatively, we could allow the first parties to impose constraints on the third party substitutes. We could add the following to the law:

> 4) Companies may impose constraints that third parties must follow if they interoperate with the company's products.
> 5) (The Constraint Constraint) These constraints must be no harder for the third party to follow than for the first party.

Without The Constraint Constraint the law would be trivial, because for example Apple could impose the constraint that devices using the iMessage protocol must be Apple devices. Some examples of constraints that pass The Constraint Constraint are:
- Third party social media frontends must display all ads
- Third party frontends must send analytics data back to the first party backend

This is one way to resolve the ad issue. It is unclear to me which version of the law would be better.

## CORS

Another interesting consequence of the law is that it would basically make CORS policies other than '*' illegal. This sounds like a dealbreaker, but I would argue that CORS is actually bad and unnecessary. Let's take a look at the security issues that CORS solves:

But there is some nuance here. CORS is enforced by the browser, and there is nothing stopping you from building a browser that ignores CORS. So in that sense CORS does not actually make interoperability impossible, since it is possible for the user to go around CORS. However, third parties can't build websites to interoperate with first party backends in this way, because all their users have browsers that do enforce CORS. So it looks like the law probably wouldn't apply here, but there could be a legal argument to be made that it does, and maybe the law should be modified so that it does.

[1]: The "i" in "iPhone" does actually stand for "involuntarily".
[2]: Or when part of their product can be substituted for an alternative without affecting the regular functioning of the remaining parts of the product. Let's not split hairs over where the hairs are split here.
