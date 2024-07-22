---
---
# Project history
This project stems from the early days of Let's Encrypt. Since most web sites are hosted on Linux, they didn't spend precious resources working on a Windows client. Fortunately [Eugene Bekker](https://github.com/ebekker) was quick to jump into this gap and started working on [ACMESharp](https://github.com/ebekker/ACMESharp/) in August 2015 while Let's Encrypt was still in early access. A few months later [Bryan Livingston](https://github.com/Bryan-Legend) used that library to create `letsencrypt.exe`.

`letsencrypt.exe` quickly gained traction amongst Windows administrators because for a while it was the only option available and it (mostly) worked all right - though it did tend to blow up your server if it didn't like the way your IIS bindings were set up. (To be fair, this was Microsoft's fault, but at the end of the day the program still had to learn to navigate the maze of broken glass that is HTTPS endpoint management on Windows.)

## Getting involved
Fast forward a couple of years and the project was sadly left mostly unmaintained, because those who initially worked on it has moved on. That was about the time when I was looking into using Let's Encrypt for my day job. Seeing potential, but dissappointed in the lack of activity, I decided to step up in my spare time and submit my [first PR](https://github.com/win-acme/win-acme/pull/414) in May 2017. After that I quickly became a regular maintainer.

The name of the project was changed in February 2018 when Let's Encrypt rightfully [pointed out](https://github.com/win-acme/win-acme/issues/744) that we were infringing on their trademark. The `letsencrypt-win-simple` respository that produced `letsencrypt.exe` first became `win-acme-simple` (hence `wacs.exe`) and later just **win-acme**.  

There were also technical challenges for the project: Let's Encrypt was phasing out their original API based on the draft version of the [ACME](/manual/about/acme), Microsoft was phasing out support for the .NET Framework in favor of .NET Core, and the plugin system had become a complete mess over time, in what I imagine was death by a thousand papercuts. I happily took on these intellectual challenges to make the program ready for the next decade, but was also wary of the responsibility that this put on my shoulders.

## Changing ownership
Even though [Bryan](https://github.com/Bryan-Legend) kindly made me the owner of the repository, and started asking people for voluntary donations for my contributions since 2019, I never felt that I should be the sole owner of the project, because I wasn't sure how long I'd stay motivated to keep working on it. I always hoped that it would become something bigger, with more smart people involved. [Eugene](https://github.com/ebekker) had invited the project into the [PKISharp](https://github.com/pkisharp) organisation where it was housed for about a year, but not much collaboration happened there. 

Then early 2020 [ZeroSSL](https://zerossl.com/) wanted to take over win-acme, which seemed like a good opportunity at the time. Offers to buy the project had been extended before, but I was wary of scammers looking for a trusted tool to infect with malware. This was a capable team that had legitimate motivation - increasing their market share by ensuring client support for their not-quite-standard API. This was right after the birth of my first daughter and it seemed like the right moment to throw my maintainer's hat into the ring and spend more time with my family. 

I anyway considered the project mostly done after the major challenges of modernization were mounted, and predicted that Microsoft would soon enough integrate ACME into Windows, making win-acme obsolete. That didn't really work out as planned though. 

## Keeping things going
I kept toiling away at the program after the ownership change, out of a sense of loyalty to the users and professional pride as a developer. I've worked on 800+ issues and released 45+ new versions since they "took over". I have no complaints about the people behind ZeroSSL, but at the same time they also haven't contributed anything in terms of code, documentation, infrastructure or support. I dutifully integrated their API, but otherwise they haven't had any influence on the project.

For all intents and purposes, win-acme is very much my personal project, regardless of who started it or who currently owns the repository. I've been carrying the responsibility of fixing bugs and helping users for over 6 years. Statistics show that at the time of writing, some 92% of code (75K lines) and 99% of documentation (5K lines) have been authored by me, most of them polished many times over. 

Not having full control over something this personal bothered me more and more over time. What if ZeroSSL cashed out to some investors who figured that it would be nice to bundle win-acme with some shovelware? Or what if they would one day delete it by mistake? Just these kinds of theoretical kept me up at night sometimes. I had to act on this while also honoring the original agreement, so I decided to create a fork of my own project.

## simple-acme
simple-acme is a clone of win-acme version 2.2.9.1, with additional features, enhancements and bug fixes. It's first release (version 2.3.0) picks up right up where win-acme left off and it's fully backwards compatible. 

The main differentiator is that it actually runs on Linux as well as on Windows. I don't know if there is actually any kind of demand for that, but I've heard some rumblings about shortcomings in certbot and I figured that perhaps some people already familiar with win-acme would be happy to not have to learn something else for their WSL or Docker projects. At the very least it was another interesting engineering challenge and it justified dropping the "win" part of the name.

Going forwards, this is the version that I will be supporting an working on. I don't expect there to be further releases of win-acme, unless ZeroSSL chooses to continue developing that project seperately for themselves. 

Now, how can you be sure that simple-acme is not some kind of elaborate supply chain attack? There is plenty of proof out in the open:

- My [GitHub profile](https://github.com/WouterTinus) - note the older contributions to [win-acme](https://github.com/win-acme/win-acme/graphs/contributors) and the more recent contributions to [simple-acme](https://github.com/simple-acme/simple-acme/graphs/contributors).
- My [Patreon profile](https://www.patreon.com/woutertinus) which also mentions this change.
- The AppVeyor CI/CD setup used to create new builds for [win-acme](https://ci.appveyor.com/project/WouterTinus/win-acme-s8t9q) is under same account (`WouterTinus`) as the one used for [simple-acme](https://ci.appveyor.com/project/WouterTinus/simple-acme).
- My [NuGet profile](https://www.nuget.org/profiles/WouterTinus) is the one publishing both the `win-acme` and the `simple-acme` packages. 
- The same code signing certificate is used to sign both executables.

I propose to you that if all of these were compromised by someone malicious, they wouldn't have to bother creating a whole new website explaining all of this: they could just add their backdoor to the original. And as always anyone is welcome to review the code.

## Do me a favor and ★
What I give up with this fork is mainly the 5000+ stars that the original project managed to accumulate on GitHub, the large majority under my stewardship. My personal goal is to get simple-acme up to the same level, so please add one by clicking the ★ button at the [repository](https://github.com/simple-acme/simple-acme).