---
layout: post
title: Thoughts on Experimental work on the norms of assertion
tags: [Cognitive Science, Paper Reading, Communication]
---

## Summary
In this research paper, the author compares animals' communication system with human's communication system
and by showing how animals evolve to detect dishonesty and prompt honest signaling with two mechanisms, the authors considers that assertion is central to human's communication and argues how the social norm of assertion should express knowledge and how the knowledge should affect people's assertions.

<!--excerpt-->

There are two mechanisms for animals to adapt honest signaling from misleading signals. The first one is that only some senders can produce certain performance signals. For instance, some performance signals is related to the signalers' body size. Only large toads can produce low-frequency sounds. This idea is similar to a concept in the computer vision or machine learning, i.e. `features`. Features, like performance signals, are unique to various groups, and even in th same community, features may vary. For example, same items look smaller at the corner under the wide-angle lens.

The second one is social policing, which is strongly associated with assertions in human's communication system. The authors uses various set of studies to verify how knowledge affect assertions, including the study of Maria's watches, whether knowledge is a simpler but stronger indicator to assertions, including the "safe for swimming" study, and when knowledge and assertions will come apart, such as "fake barn" cases. These studies are trying to build a link between knowledge and assertions, and help us understand how knowledge could not only affect decision making and trust, but also have an influence on the feedback, which leads me to think about a popular network nowadays in the artificial intelligence, i.e. the generative adversarial network (`GAN`).

From my understanding, the GAN can be generally considered as two parts, a generator and a discriminator. If we take the whole network as a communication system, we could say that the discriminator is more likely to be the one that will make the assertion based on the current knowledge and the generator is a receiver that responds to the assertions and update the knowledge of itself and the discriminator. We feed the discriminator with a large amount of data (knowledge), and let the generator try to fool the discriminator with the generated assertion. If the assertion originally can be quickly identified as "fake", and the generator keep receiving this updated knowledge for several iterations, it will know how the "true" assertion looks like, and generate a plausible assertion, which is certain or even true based on the knowledge of the discriminator. This knowledge-assertion idea helps better understand why and how GAN works in a more intuitive and philosophical perspective.

Regarding the limitations, the author admits those experiments are regionally limited and needs to conduct more experiments across culture. Communication itself is complex and becomes more complicated when it happens between groups of different culture. One example is that Asian culture focus on more implicit communication while western culture is more direct, so sometimes people may not find any knowledge in the assertions between Asian people.