# paypackage - paying for packages via package management systems
Open discussion on issues related to the idea of voluntarily paid OSS usage through package management subscriptions.

The objective of this repo is to correlate ideas for approaches to paying maintainers, via package management, with an emphasis on simplicity.

Large and small organisations make use of millions of open source packages/modules daily. Largely these packages are not being paid for and are provided free of charge via distribution through package managers such as npm and NuGet.

Developer systems, build servers etc. currently use the infrastructure provided by these package managers for free, resulting in the cost burden being entirely handled by the package manager systems.

Package maintainers and contributors are generally not financially rewarded for their work on the packages, unless they are developing the package through the course of their normal employment or their package is related to a commercial service they operate.

## How do open source package maintainers currently get paid?
Currently a variety of funding platforms exist, such as Open Collective. Most of these platforms rely on individual developers or kind hearted organisations making donations/ad-hoc payments. The organisers of the particular group benefiting from the donations then decides how to distribute the funds as expenses. Well-known packages do managed to achieve credible funding using this approach (e.g. webpack). Unknown packages (which may be depended on by the more widely known packages) are not directly rewarded.

Such platforms require organisations to opt-in to payment for packages they use (or support) and to nominate a donation amount based on what the organisation feels like paying. Occasionally organisations will pay a larger amount to appear as major sponsors.

## How can package management platforms pay maintainers?
The following model is a broad suggestion as to how package management platforms could financially rewards developers and fund their own service operations.

# Package Management Subscriptions

## Onboarding organisation via developers
The developer of a software application begins building his app using common tools. When installing a recommended package to achieve this task the package manager console shows the message `If using this package for development of a commercial application (for a business), please configure your organisations subscription key in your package manager.`. This could be referred to as 'nag-ware', as the developer is not obstructed from using the software, but compelled to enroll his organisation in the subscription system.

The developer then informs his project manager/line manager that they need to use this package (and it's dependencies) and should get a subscription to the package management system. The developer provides a referral link and as soon as his organisation sets up their billing for the subscriotion

The organisation creates a subscription with the package management system (or a 3rd party which manages this for them). The organisation will now pay monthly for all package usage. 

## Why will the organisation join?
The organisation will most likely join because the developer said they needed to. If the developer does not state it as a requirement to the organisation then they will not join. Some organisations will resist joining, others will join willingly. Compared to the status quo, there is no new disadvantage to the package owner/platform if an organisation fails to join.

## Billing

- Organisations can issue keys from their subscription and add arbitrary tagging of keys to indicate usage
- Spending would be tracked per authenticated download using the api/developer key so that it can be attributed to either developers, project cost codes or build servers etc as required by the organisation.
- The monthly bill is not a donation to a project, it is payment for a service.

## Cost calculation

- Authenticated package downloads will be charged at a stated rate
- Authenticated package cache hits will be charged at a stated rate
- Package downloads may cost less for popular packages (as disk space/data transfer also does in volume)
- Costs count against all package dependencies, not just the top level package.
- Packages not opt-ed in to the earning will have their monthly earnings absorbed by the platform in exchange for hosting.

## Earnings
- Package download earnings for popular packages could be substantial e.g webpack $0.01 USD per download for ~1M per day = $10,000 
- free/discounted downloads for registered charities? (although there is no enforced need for them to subscribe at all)
- package management system will take a standard % from package earnings to fund their services.
 
### Advantages
- Simple monthly billing for the organisation related to their own usage.
- Already a familiar model for organisations with cloud subscriptions
- Only one cost justification exercise
- Package owner gets funded and can distrubted to maintainers.
- Package management system gets funded

### Problems

The following issues are the most obvious:
- Would cached use of a package from a local package manager cache count or not? It probably should count in some way but perhaps not as much as full download.
- Disputes over package ownership will be resolved through unspecified means.
- Disputes over rewards to contributors will be resolved through unspecified means. Possibly the package manager needs to hold funds when code contributions become disputed and standard process for abitration would be required.
- Forking a package, re-branding it and then promoting it to achieve higher usage means the original package owner loses out. This may need to be actively discouraged or a penalty system introduced  e.g.:
  - a dispute has been raised, your package is 90% similar to x, so 90% of your earnings will go to x until that changes etc.
