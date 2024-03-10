# 0 - Intro

I'm not a great painter and I don't think I've ever won a game of 40k, but I'm a data analyst/data scientist and I absolutely loved the series. I was up to about book 4 when I realised that the series itself was long enough and granular enough to be a dataset. Bought all the ebooks as I was reading them and essentially tagged each section with characters' perspectives; this exercise is pretty trivial for other series like WoT or ASOIAF because chapters are named after their characters' perspective, but here's the Horus Heresy changing perspectives multiple times in each chapter, and on a few occasions, in a single sentence (looking at you Dan Abnett).

What I'm left with is 7,180 instances of perspectives for 739 characters total. Worth mentioning this is *all* characters, including ones whose perspective lasts a few words until they're squished by a Space Marine (or, in one very specific instance, from a knife's perspective). The dataset is open and available at the link in csv format, with book number, chapter number, perspective number (i.e., from 1 to x based on where their perspective is in the chapter), whose perspective it is, and total word count. Hopefully there's no copyright issues here, I've only released book and character names/affiliations. Final note: I've included short stories in this analysis; there's an argument for excluding them since they can skewa few of the results, but they are an important part of the narrative, they're often used to bridge certain events together meaning characters often appear in short stories as well as longer books, and some of them absolutely slap so worth keeping in.

With that out of the way, let's dig into the data!

# 1 - Overview

The Horus Heresy is *long*, clocking in at about 7,484,862 words. For reference, ASOIAF is around 1.8 million words and the Wheel of Time is around 4.4 million words (according to [this site](https://loopingworld.com/2009/03/06/wordcount/)). This is split across 64 books (which, for you Chaos conspiracy theorists, is 8*8) for an average of 116,951 words per book. This is also 1,042 average words per perspective, and 10,099 words per character.

**Table 1a. Word count by species**
| Species          | words     |     % |
|:-----------------|:----------|------:|
| Astartes         | 3,935,534 | 53.73 |
| Human            | 1,816,649 | 24.8  |
| Primarch         | 1,037,570 | 14.17 |
| Perpetual        | 251,923   |  3.44 |
| Custodes         | 137,261   |  1.87 |
| Daemon           | 54,324    |  0.74 |
| Pariah           | 50,272    |  0.69 |
| Eldar            | 15,864    |  0.22 |
| Thunder Warriors | 11,082    |  0.15 |
| Knife            | 9,540     |  0.13 |
| Progenitor       | 4,089     |  0.06 |
| Lacrymole        | 358       |  0    |
| Tyranids         | 198       |  0    |

I've loosely classified the 'species' of each perspective in Table 2a; species probably isn't the right word, but it's enough to show the difference between humans, Astartes, and Primarchs. Unsurprisingly the Astartes lead with just over 50% of the total perspectives, and a whopping 3.9 million words total. Humans are half that at 1.8 million, but for reference, that means the total human perspectives in the Horus Heresy are as long as ASOIAF. Primarchs have a good showing at just over a million words, and down the bottom we have interesting segments like 'Progenitor', 'Lacrymole', and 'Tyranids'. Oh, and 'Knife'; yes there is a section of this series that's from the perspective of a knife.# 2 - Characters

The top character is Loken with 217,993 words, around 2.91% of total words in the series. For reference, Loken's perspective takes up approximately 1.86 books based on average length per book.

**Figure 2a. Top 10 characters by total words**
![A bar chart showing the top 10 characters by word count. The top is Loken, followed by Zahariel, Garro, Ahzek Ahriman, Sanguinius, Abaddon, Corvus Corax, Vulkan, Kasper Hawser, and Oll Persson.](https://github.com/sklavoug/horus_heresy_analysis/blob/main/2a%20-%20Top%2010%20Chars.png?raw=true)

Interestingly, the top 10 characters by total words (figure 2a) is quite diverse. There are 5 Astartes, 3 Primarchs, a Perpetual, and a random human. This doesn't *quite* align with the overall stats by species (see Table 2a), but it's correct on Astartes at least. The top words are only part of the story part of the story for characters, however. If we look at the same characters by words per book, a different picture emerges.

**Figure 2b. Top 10 Chars (Most Words) by Avg Words per Book**
![A bar chart showing the top 10 characters by word count, by average words per book. Kasper Hawser is almost 3 times as prominent as the next highest, Corvus Corax.](https://github.com/sklavoug/horus_heresy_analysis/blob/main/2b%20-%20Top%2010%20Chars%20(Most%20Words)%20by%20Avg%20Words%20per%20Book.png?raw=true)

In this case, we can see Kasper Hawser is almost 3 times further ahead than the next character. This makes a lot of sense -- Kasper Hawser basically has his own book in which he is really the only perspective, whereas even Loken -- who has the most words in the entire series -- is spread across quite a few books.Notably this is the top 10 by total words; let's see what it looks like when we use words per book as the metric to decide the top 10.

**Figure 2c. Top 10 Chars (Avg Words) by Avg Words per Book**
![alt text](https://github.com/sklavoug/horus_heresy_analysis/blob/main/2c%20-%20Top%2010%20Chars%20(Avg%20Words)%20by%20Avg%20Words%20per%20Book.png?raw=true)

Uh, ok. This is...interesting. I know Kasper Hawser, Kai Zulane, and Archamus. But uh...who are the rest of these people? Anton Galba? Dalia Cythera was in 'Mechanicum' I'm pretty sure. Dravian Klayde? Corvus Corax? Oh wait I do know him. Pretty sure Lysimachus is an Imperial Fist? Meros is the Blood Angel madlad, and Zenobi is the true Arch-Traitor. This is an interesting dynamic, as while I know exactly who the top 10 are by total words, I have to really think about the top 10 by average words per book. Kasper Hawser has more words per book than any other character, but he's only in one book: his perspective is *focused*. But in a series with 64 books, characters who appear in multiple books tend to have more impact, since they're just present at more events (e.g., the Long Companions, Erebus, etc.).

There's one other aspect to this that relates closely to avg words per book, and that's average *proportion* of book this character occupies. This one's going to be a bit different since we're getting away from total words, and taking averages of percentages is a bit weird (e.g., they might have 10,000 words in a really long book and make up 1% and 10 words in a super short book and make up 10%), but it's more a check of the breadth of their perspective.

**Figure 2d. Top 10 Chars by Proportion of Book**
![alt text](https://github.com/sklavoug/horus_heresy_analysis/blob/main/2d%20-%20Top%2010%20Chars%20by%20Proportion%20of%20Book.png?raw=true)

Now we're back in familiar territory; interestingly 8 of the top 10 characters by total words make up the top 10 by proportion of book, with Zahariel and Garro featuring twice for 2 books. This is interesting as there's not necessarily a relationship between total words and proportion of words in book; Oll Persson is a good example of this, as he's in the top 10 total words but only appears on the list of proportion of book at number 57 with 19.5%. What this demonstrates is that most of the top 10 by words tend to have at least one book centred on them.

Let's wrap up characters with a look at avg length of perspective vs number of books the character has appeared in. This gives me a chance to make a quadrant graph (yay!) and label each of the quadrants. Our top right is going to be 'Protagonists': these are characters with long perspectives and frequent appearances, they're the real mainline perspectives throughout the series. Bottom right is 'Lore Dump': these are characters with long perspectives and infrequent appearances, so they more act as one-and-done insights into particular areas (like Kasper Hawser for the Space Wolves, or Dalia Cythera for the Mechanicum). Bottom left is 'Incidental', which is most of the characters: short perspectives and infrequent appearances. I'm going to set a threshold for featuring on this chart, because otherwise it'll just be a bunch of circles in the bottom left. And finally, in the top left quadrant will be 'Hand of Destiny': short perspectives and frequent appearances. The main one I'm thinking of here is Erebus (duh), because this category is for characters who we aren't necessarily following through the series (like the Protagonists), but for characters who are subtly or unsubtly making an impact on events at key points. Did I just want to make this graph so I could label one of the quadrants 'Hand of Destiny'? Yes, absolutely.

**Figure 2e. Characters by Avg Words and Books**
![alt text](https://github.com/sklavoug/horus_heresy_analysis/blob/main/2e%20-%20Characters%20by%20Avg%20Words%20and%20Books.png?raw=true)

Interesting, another unexpected result! The Protagonists are pretty sparse: just Sanguinius, Abaddon (???) and Loken. Loken and Sanguinius I get, they both have a lot of perspectives, but Abaddon is an interesting one; although I guess he features a lot in the back end? Regardless, the lore dumps in the bottom right are also about right: Zahariel, Ahriman, Garro, and Corax; one member of each of the less-explored Legions, although Zahariel did appear in 7 books overall (I think he's more protagonist but might have been undermined by a few short stories). Bottom left isn't worth going into, although there are a few Primarchs in there. And finally, the Hand of Destiny, which is honestly more crowded than I thought it would be. John Grammaticus and Oll Persson are both in there which makes sense (John slightly higher which kinda reflects that he's doing more actual influencing than Oll), Sigismund (makes sense), Erebus (duh, it's named after him), Malcador and Rogal Dorn (yup definitely, they're on Terra for the whole series), and Horus! The big H himself is in the Hand of Destiny category, which honestly makes perfect sense: he has a lot of snippets at the end of books where he broods, and is bumped up in words by the opening trilogy and final arc, so that does make sense.

Well that about wraps up the characters, it's on to part 3: the Legions!
