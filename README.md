# 0 - Intro

I'm not a great painter and I don't think I've ever won a game of 40k, but I'm a data analyst/data scientist and I absolutely loved the series. I was up to about book 4 when I realised that the series itself was long enough and granular enough to be a dataset. Bought all the ebooks as I was reading them and essentially tagged each section with characters' perspectives; this exercise is pretty trivial for other series like WoT or ASOIAF because chapters are named after their characters' perspective, but here's the Horus Heresy changing perspectives multiple times in each chapter, and on a few occasions, in a single sentence (looking at you Dan Abnett).

What I'm left with is 7,180 instances of perspectives for 739 characters total. Worth mentioning this is *all* characters, including ones whose perspective lasts a few words until they're squished by a Space Marine (or, in one very specific instance, from a knife's perspective). The dataset is open and available at the link in csv format, with book number, chapter number, perspective number (i.e., from 1 to x based on where their perspective is in the chapter), whose perspective it is, and total word count. Hopefully there's no copyright issues here, I've only released book and character names/affiliations. Final note: I've included short stories in this analysis; there's an argument for excluding them since they can skewa few of the results, but they are an important part of the narrative, they're often used to bridge certain events together meaning characters often appear in short stories as well as longer books, and some of them absolutely slap so worth keeping in.

With that out of the way, let's dig into the data!

# 1 - Overview

The Horus Heresy is *long*, clocking in at about 7,484,862 words. For reference, ASOIAF is around 1.8 million words and the Wheel of Time is around 4.4 million words (according to [this site](https://loopingworld.com/2009/03/06/wordcount/)). This is split across 64 books (which, for you Chaos conspiracy theorists, is 8*8) for an average of 116,951 words per book. This is also 1,042 average words per perspective, and 10,099 words per character.

# 2 - Characters

The top character is Loken with 217,993 words, around 2.91% of total words in the series. For reference, Loken's perspective takes up approximately 1.86 books based on average length per book.

**Figure 2a. Top 10 characters by total words**
![alt text](https://github.com/sklavoug/horus_heresy_analysis/blob/main/2a%20-%20Top%2010%20Chars.png?raw=true)

**Table 2a. Word count by species**
| Species          |            words |     % |
|:-----------------|-----------------:|------:|
| Astartes         |      3.93553e+06 | 53.73 |
| Human            |      1.81665e+06 | 24.8  |
| Primarch         |      1.03757e+06 | 14.17 |
| Perpetual        | 251923           |  3.44 |
| Custodes         | 137261           |  1.87 |
| Daemon           |  54324           |  0.74 |
| Pariah           |  50272           |  0.69 |
| Eldar            |  15864           |  0.22 |
| Thunder Warriors |  11082           |  0.15 |
| Knife            |   9540           |  0.13 |
| Progenitor       |   4089           |  0.06 |
| Lacrymole        |    358           |  0    |
| Tyranids         |    198           |  0    |

Interestingly, the top 10 is quite diverse. There are 5 Astartes, 3 Primarchs, a Perpetual, and a random human. This doesn't *quite* align with the overall stats by species (see Table 2a), but it's correct on Astartes at least (and yes, I did put 'Knife' as a species). The top words are only part of the story part of the story for characters, however. If we look at the same characters by words per book, a different picture emerges.
