Yesterday I ran a Diversifying Devops
Workshop, http://www.eventbrite.com/e/diversifying-devops-workshop-registration-16625204434,
in Arlington. The idea came from a discussion on the DevOpsDC Meetup planning
team on how to make our Meetups less homogeneous, and we decided to invite
people from underrepresented communities to get introduced to DevOps.

I volunteered to run the workshop, and mashed together materials from the Chef
training decks, CI/CD workshop, and what I thought people should know about
Git, GitHub and AWS.

We had 14 people from a wide range of backgrounds show. A few people were no-shows, which was OK since I was plenty busy with those who did show up.

I set the goals of the workshop as follows:

- Enough Chef to run a static webpage
- Enough Git & GitHub to collaborate
- Enough testing to collaborate reliably
- Enough AWS to operationalize our site

The feedback was uniformly positive and strong, participant rating the day as among their best professional development experiences.

And I did a few things experimentally that worked out pretty well. In no particular order:

Having slides in Markdown and rendered with Reveal:

- Slides as versionable code FTW
- Fewer code errors since there's nothing trying to turn 'code' into ‛code’
- Slides were browseable in real-time at slides.devopsdc.com:1948
- Slides are completely printable as regular html, e.g., https://github.com/devopsdc/intro2devops/blob/master/slides/lab-1_resources.md

Adding some elements of delight:
- I used Fluxx cards to designate which subdomains each pair would work on. e.g.,
  - ws.peace.devopsdc.com
- Installing `cowsay`, `fortune` and `sl` as Easter Egg packages instead of `vim` and `emacs`


Having a domain: devopsdc.com
- Made it all seem more real
- the new route53 cookbook is a big win as nodes can self-register DNS in Route53 w/o having to into build-essentials/nokogiri hell (https://github.com/hw-cookbooks/route53/pull/70)

Making Git and GitHub core to the process
- Each pair worked against their own repo e.g. https://github.com/cheffian/sun
- Doing real code reviews and PRs
- branching and committing your work

Emphasising the introductions not as mere formality but core the day's objectives.
- DevOps is about trust & communication
- Screens closed and 10-12 minutes in groups of four, then round-robin introductions to the rest of the class
- Rest of the day was very engage and collegial

Making pairing primary
- Necessary for PRs
- Each pair had a shared workstation (ws.(fluxxcard).devopsdc.com) and dev host (dev.(fluxxcard).devopsdc.com)
- It turned out that simultaneous kitchen-docker runs would kill the shared workstation, so that further encouraged pairing (an untended but happy consequence).

Some acknowledgements
- Jennifer Davis for encouragement, suggesting pairing, and stickers
- Christine Hersh for feedback and initial content run-through
- James Scott for slides in Reveal
- Bryan Johnson for Jenkins CI/CD stuff
- Irving Popovetsky for giving me the time (not that I asked, but he would have said
  "Yes" if I had asked)
- Franklin Webber for exemplifying how to live code while explaining one's thought
  process.
- Nathen Harvey for being, you know, Nathen
- Wendy McIntosh for heading up the diversity initiative here
- Tyler Ball and John Keiser for getting Chef Provisioning to the point where
  I can rely on it for workshop setup.

References:
- Workshop Cookbooks and Code: https://github.com/cheffian/fluxx
- Workshop Slides and Labs: https://github.com/devopsdc/intro2devops
- Markdown & Reveal: https://github.com/webpro/reveal-md
- Fluxx cards: http://www.looneylabs.com/games/fluxx
