# paypackage
## paying for packages via package management systems
Open discussion on issues related to the idea of voluntarily paid OSS usage through package management subscriptions.

The objective of this repo is to correlate ideas for approaches to paying maintainers, via package management, with an emphasis on simplicity.

Large and small organizations make use of millions of open source packages/modules daily. Largely these packages are not being paid for and are provided free of charge via distribution through package managers such as npm and NuGet.

Developer systems, build servers etc. currently use the infrastructure provided by these package managers for free, resulting in the cost burden being entirely handled by the package manager systems.

Package maintainers and contributors are generally not financially rewarded for their work on the packages, unless they are developing the package through the course of their normal employment or their package is related to a commercial service they operate.

## How do open source package maintainers currently get paid?
Currently a variety of funding platforms exist, such as Open Collective. Most of these platforms rely on individual developers or kind hearted organizations making donations/ad-hoc payments. The organizers of the particular group benefiting from the donations then decides how to distribute the funds as expenses. Well-known packages do managed to achieve credible funding using this approach (e.g. webpack). Unknown packages (which may be depended on by the more widely known packages) are not directly rewarded.

Such platforms require organizations to opt-in to payment for packages they use (or support) and to nominate a donation amount based on what the organization feels like paying. Occasionally organizations will pay a larger amount to appear as major sponsors.

## How can package management platforms pay maintainers?
The following model is a broad suggestion as to how package management platforms could financially rewards developers and fund their own service operations.

# Package Management Subscriptions

## On-boarding organizations via developers

The developer of a software application begins building his app using common tools. When installing a recommended package to achieve this task the package manager console shows the message:

> A subscription is required if using this package for the development of a commercial application (for a business), please configure your organizations subscription key in your package manager.

This could be referred to as a 'nag-ware' license, as the developer is not obstructed from using the software, but compelled to enroll his organization in the subscription system. This is commonly referred to a 'Asking for the Sale' and is the single most key step in converting a free user to a paid user.

The developer then informs his project manager/line manager that they need to use this package (and it's dependencies) and should get a subscription to the package management system.

The organization creates a subscription with the package management system (or a 3rd party which manages this for them). The organization will now pay monthly for all package usage. The organization can now issue authentication keys to use their subscription.

## Why will the organization join?

The organization will most likely join because the developer said they needed to. If the developer does not state it as a requirement to the organization then they will not join. Some organizations will resist joining, others will join willingly. Compared to the status quo, there is no new disadvantage to the package owner/platform if an organization fails to join.

## Billing

- Organizations can issue keys from their subscription and add arbitrary tagging of keys to indicate usage
- Spending would be tracked per authenticated download using the API/developer key so that it can be attributed to either developers, project cost codes or build servers etc as required by the organization.
- The monthly bill is not a donation to a project, it is payment for a service.

## Cost calculation

- Authenticated package downloads will be charged at a stated rate
- Authenticated package cache hits will be charged at a stated rate
- Package downloads may cost less for popular packages (as disk space/data transfer also does in volume)
- Costs count against all package dependencies, not just the top level package.
- Packages not opt-ed in to the earning will have their monthly earnings absorbed by the platform in exchange for hosting.

## Opting out or donating

- By default making your package 'paid' would be opt-in. So if your project doesn't want to earn money (for any reason) then it doesn't. Download fees etc will be rated as 0 by the package management billing platform, no prompt for payment will appear during installs etc.
- If you want to earn where possible but then donate all the proceeds to charity (such as Open Collective) then you would opt-in and configure this via the package management billing platform. This may be preferable for projects that can't agree on how funding should be distributed, they can just opt-out.

## Earnings

- Package management system will take a standard % from package earnings to fund their services.
- Package download earnings for popular packages could be substantial depending on the % of users
converted, e.g `1M downloads per day of webpack @ $0.01 USD = $10,000`
- Earnings allocated to the package are controlled by the package owners. They can opt to donate to charity, collect the funds themselves or a mixture. 

## Contributor Earnings
- Contributors must opt-in to receive an allocation based on their contributions (projects may manually allocate % or use documented source control/issue management activity etc).
 
## Advantages

- Simple monthly billing for the organization related to their own usage.
- Already a familiar model for organizations with cloud subscriptions.
- Only one cost justification exercise.
- Package owner gets funded and can distributed to maintainers. 
    - Ongoing maintenance for commonly referenced packages is unlikely to be a long term problem.
- Package management system gets funded.
- Not being able to pay does not disadvantage a developer.

## Problems

The following issues are the most obvious and may vary by package management platform:

Would cached use of a package from a local package manager cache count or not? It probably ideally count in some way but perhaps not as much as a full download. *Downloads only* would be the fallback position.

Disputes over package ownership will be resolved through unspecified means. One option is for the package management system to provide notice to contactable contributors, if the majority reject the notion then the package cannot opt-in. 

Disputes over rewards to contributors will be resolved through unspecified means. Possibly the package manager needs to hold funds when code contributions become disputed and a standard process for arbitration would be required. Alternatively individual contributors may register and opt to receive a portion of funding based on their commits.

Forking a package, re-branding it and then promoting it to achieve higher usage means the original package owner loses out. This may need to be actively discouraged or a penalty system introduced  e.g.:
  - a dispute has been raised, your package is 90% similar to x, so 90% of your earnings will go to x until that changes etc.
  
Copying (not forking) a package and re-branding it may be allowed by your current package/library license. In the future people may decide to choose licenses with copyright restrictions to safeguard their rights as a contributor, this may in turn affect whether or not other packages choose them as a dependency.

In all cases, non-resolvable disputes would be resolved by opting out the package, returning it to the free model.

Topics involving money create conflict and this proposed model will be no different. Legal disputes will happen. If in doubt, opt-out.

Other aspects of the model may be considered too naive, please raise an issue with the scenario that's not covered.

## Frequently Asked Questions

**Q: I have a complex or subtle scenario this model does not cover**

A: If your scenario cannot be covered by opting-out or donating proceeds, please raise an issue.

**Q: This is a dumb idea**

A: Do not opt-in.

**Q: My popular package is mostly copy and pasted from other peoples work and bits of Stack Overflow**

A: Do not opt-in, unless you've shuffled it around a bit and renamed all the variables (joke). Either way money vs. copyright do not mix well. Donating all the proceeds to charity may be agreeable to unwitting contributors. The safest option in this case is to not opt-in. This is not legal advice and IANAL.

**Q: This would be too complex and expensive to implement for my package management platform.**

A: Do not implement the model, or start/use an open source solution.

**Q: I don't want to do this but my downstream dependencies are opting in and making million.**

A: You should opt-in and see how it goes. You can opt-out later.

**Q: I don't want to do this but a bunch of my contributors want paid.**

A: You can opt-in and donate your allocation of the proceeds.

**Q: I gave my package to someone else to maintain, now they will make millions.**

A: You can opt-in to receive your allocation as a contributor.

**Q: My library was removed as a dependency from a popular package. I'm losing a lot of money.**

A: This is an unfortunate side-effect of the model.

**Q: My library was copied into a popular package so it's no longer a dependency. I'm losing a lot of money.**

A: If your library license allowed this then there is likely nothing you can do except raise this publicly for the maintainers to morally defend.

**Q: Most organizations won't pay.**

A: That's OK. The packages are free by default and are only compelling users to pay. A percentage of users will pay, and that percentage will be higher than zero.

*Discussions, suggestions, PRs welcome.*
