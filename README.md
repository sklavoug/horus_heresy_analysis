# 0 - Intro

I'm not a great painter and I don't think I've ever won a game of 40k, but I'm a data analyst/data scientist and I absolutely loved the series. I was up to about book 4 when I realised that the series itself was long enough and granular enough to be a dataset. Bought all the ebooks as I was reading them and essentially tagged each section with characters' perspectives; this exercise is pretty trivial for other series like Wheel of Time or A Song of Ice and Fire because chapters are named after their characters' perspective, but here's the Horus Heresy changing perspectives multiple times in each chapter, and on a few occasions, in a single sentence (looking at you Dan Abnett).

What I'm left with is 7,180 instances of perspectives for 739 characters total. Worth mentioning this is *all* characters, including ones whose perspective lasts a few words until they're squished by a Space Marine (or, in one very specific instance, from a knife's perspective). The dataset is open and available in the 'data' folder. Hopefully there's no copyright issues here, I've only released book and character names/affiliations which is less information than the wiki pages have (see the appendix for more detail on what's included in each of the csv files). Final note: I've included short stories in this analysis; there's an argument for excluding them since they can skew a few of the results, but they are an important part of the narrative, they're often used to bridge certain events together meaning characters often appear in short stories as well as longer books, and some of them absolutely slap so worth keeping in.

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

 # 3. Legions
Although the series features characters from all sorts of backgrounds, species, and affiliations, it's absolutely a story about the Astartes. The Space Marines occupy just over 50% of the series with their perspectives, although if you include the Primarchs they're over 2/3rds of the series (as seen in Table 2a). Each of the Astartes (barring one character) are descended from one of 18 Legions, which aren't necessarily equally represented.

**Figure 3a. Sum of words by Legion**
![alt text](https://github.com/sklavoug/horus_heresy_analysis/blob/main/3a%20-%20Sum%20of%20words%20by%20Legion.png?raw=true)

Figure 3a shows the sum of words per Legion, with the Sons of Horus being top with over 500K, followed by the Dark Angels with 330K and the Ultramarines with 308K. Without a doubt, the lowest are the Night Lords (81K) and Alpha Legion (54K). It's worth noting here that the Alpha Legion makes sense as we rarely actually see their perspective, and interact far more with their human agents or Alpharius/Omegon; it's similar for the Night Lords, as the majority of their story is told via Konrad Curze himself. If you include non-Astartes characters for these factions, their totals increase to 171K for the Alpha Legion and 99K for the Night Lords.

Enough about the bottom 2 though, let's dig into the other legions a bit here. First off, a note on methodology. I said above that the Astartes are 'descended' from one of the 18 Legions; this is very deliberate wording, as saying they're 'members' of a Legion would make it tricky to define characters like Loken and Garro, who forsake their Legion and actively fight against them. The Knights-Errant create a bit of an issue when trying to straighten out this dataset, as they a) feature quite prominently, and b) are prevalent enough that they do change the figures for a few Legions overall (just remember how much Loken content is in the Siege of Terra). In the end I've included them in most analysis for their parent Legion, which is for a couple of reasons. The first is the idea that they are 'biologically' a part of that Legion, in that they have their primarch's gene-seed whether they like it or not. If there were a virus that only targeted Mortarion's DNA, then Garro would be caught up in it just like the rest of the Death Guard (although he'd probably be the only one affected since the DG are already pretty messed up biologically). As well, from a narrative perspective, these characters' sections do deal a lot with what it means to stand apart from one's Legion. Loken with the Sons of Horus, Garro with the Death Guard, and Tylos Rubio with the Ultramarines: they're all off doing Sigillite-y things, but a lot of their sections involves them thinking about and grappling with their Legion and their history. If they renounced their Legion and then just never thought about them again, it'd be harder to argue that they should still be included in those Legions' results. But from the core idea that a Legion's perspective represents their prevalence in the Heresy, and how much the Heresy is their story, then the Knights-Errant still fit with their original Legions.

Tl;dr: The Knights-Errant are included in their original Legion by default and will be flagged when they've been excluded. Continuing on with the Legions, we can look at how many books they appear in and average out their words (much like the previous section), but we have another dimension here which is number of characters for each Legion.

**Table 3a. Words per book and per character by Legion**
| Affiliation       |   Number of Books |   Number of Characters |   words |   Avg_per_book |   Avg_per_char |
|:------------------|------------------:|-----------------------:|--------:|---------------:|---------------:|
| Alpha Legion      |                 5 |                      8 |   54094 |          10819 |           6762 |
| Blood Angels      |                16 |                     23 |  175539 |          10971 |           7632 |
| Dark Angels       |                16 |                     12 |  334264 |          20892 |          27855 |
| Death Guard       |                14 |                     19 |  244673 |          17477 |          12878 |
| Emperors Children |                15 |                     17 |  185356 |          12357 |          10903 |
| Imperial Fists    |                21 |                     24 |  232240 |          11059 |           9677 |
| Iron Hands        |                14 |                     30 |  260433 |          18602 |           8681 |
| Iron Warriors     |                12 |                     18 |  156848 |          13071 |           8714 |
| Night Lords       |                 9 |                      9 |   81630 |           9070 |           9070 |
| Raven Guard       |                11 |                     17 |  158575 |          14416 |           9328 |
| Salamanders       |                12 |                     28 |  262325 |          21860 |           9369 |
| Sons of Horus     |                30 |                     28 |  536641 |          17888 |          19166 |
| Space Wolves      |                16 |                     18 |  133109 |           8319 |           7395 |
| Thousand Sons     |                11 |                     14 |  247666 |          22515 |          17690 |
| Ultramarines      |                19 |                     43 |  308153 |          16219 |           7166 |
| White Scars       |                13 |                     12 |  165402 |          12723 |          13784 |
| Word Bearers      |                25 |                     37 |  281941 |          11278 |           7620 |
| World Eaters      |                15 |                     14 |  116645 |           7776 |           8332 |

Interestingly, it doesn't seem like there's a relationship between number of characters, number of books, and total words. The Night Lords and Alpha Legion have the lowest of both, sure, but the Dark Angels only feature in 16 books with 12 characters and are the second-highest in terms of total words. The DA are also the highest in terms of average words per character (unsurprising since Zahariel occupies a huge chunk of the series), but the highest averages per book are the Thousand Sons and Salamanders who are both relatively low in terms of average per character. This is an interesting dynamic; much like before when we looked at characters, there's a balance between the Legions in terms of number of characters, number of books, and total words. I smell another quadrant chart!

**Figure 3b. Legions by number of books and characters**
![alt text](https://github.com/sklavoug/horus_heresy_analysis/blob/main/3b%20-%20Legions%20by%20number%20of%20books%20and%20characters.png?raw=true)

Interesting! I was planning to label these just like the last quadrant chart, but the results kind of speak for themselves since over half the Legions are in the bottom left quadrant. This reflects how extreme the difference is between the prominent Legions and those that appear less often; case in point, in a 64-book series the Sons of Horus appear in just under half the books in one way or another. Surprising? I was surprised too! But remember that a lot of books involve an incidental Horus/Abaddon perspective, either in Lupercal's Court on the Vengeful Spirit, or out and about. The other three Legions in the top right also make sense, in their own way: Ultramarines, Word Bearers, and Imperial Fists. They're all quite unique in terms of their story and the structure of their perspectives, but it does make sense why they're in the top right: the Ultramarines have a lot of focus during the Imperium Secundus arc, and are so populous that they feature in a lot of books as a one-off perspective (worth noting too they have the most characters overall, which is unsurprising). The Word Bearers have a kind of proto-Sons of Horus effect; they have a lot of named characters but most of them only exist in a single book as 'antagonists' to be thwarted. They're the overwhelming bad guys of the series, as unlike the Sons of Horus -- who are canonically one of the best Legions -- the Word Bearers have no shortage of weird chaos culty chaff to grandstand and monologue and scheme and invariably be slain in the second-last chapter. And finally there's the Imperial Fists; unlike the others they're not really that involved in the Heresy until the very end, but they feature a lot as quick snapshots of what they're up to in terms of fortifying Terra.

The top left is interesting as well: these are Legions that have more than average characters but appear in fewer books. Again, this makes sense for different reasons: the Blood Angels are in Imperium Secundus and feature a lot in the Siege of Terra (keeping in mind this doesn't include Primarchs). The Iron Hands are out there sticking it to the traitors, so they have a lot of perspectives around the middle with the Shattered Legions. And the Salamanders are similar to the IH, they're in the Shattered Legions, but they also have a lot more books purely focused on their perspective and have Vulkan's entire arc.

Looking at the Word Bearers has given me an idea actually; we should look at the books per character for each Legion. This is an extra level of aggregation, but I think it'd be interesting. I also think it'd be good to know how far from the end of a book are characters' final appearance -- this seems niche, but I'm mostly curious because I know the Word Bearers tend to be villains so they usually die a chapter or two before the end, and I also know the IF and SoH get a lot of final chapter asides throughout the series so I'm wondering if that's reflected. Last one, let's look at chapters per book per Legion, since I think this will show the SoH dropping down as they're more tangential.

**3c. Average chapters per book by legion**
![alt text](https://github.com/sklavoug/horus_heresy_analysis/blob/main/3c%20-%20Avg%20Chapters%20per%20Book%20by%20Legion.png?raw=true)
From Figure 3c we can see that the Salamanders and Thousand Sons are the top Legions in terms of chapters per book, at over 20 chapters on average each -- makes sense since the Thousand Sons and Salamanders tend to be the sole participants of books they're in. The next 3 are the Iron Hands, Ultramarines, and Sons of Horus, which does make sense as they tend to be protagonists in a few books but feature in a lot of others. This metric also isn't perfect -- most notably it's dependent on how many chapters a book has, and there's definitely a Salamanders book with 60 chapters in there somewhere which would skew their average. But it presents a different way to view the data and shake up the rankings, as the Sons of Horus are in 5th place here, and notably, the bottom 2 in this chart are the Space Wolves and World Eaters (as opposed to the Night Lords and Alpha Legion, who are still low but not at the very bottom here).

So yeah, I guess that about wraps up my analysis. Not much else to talk about here, just characters and Legions...nah just kidding, let's get to what you're really here for: the Primarchs!

# Appendix
**Column names and descriptions in perspective_words.csv**
| Column         | Desc                                                                                                                                                                                                                                                               |
|:---------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Book_Num       | Book number in the series                                                                                                                                                                                                                                          |
| Chapter_Num    | Chapter number in the current book                                                                                                                                                                                                                                 |
| Section_Num    | Section number in the chapter (I don't recommend using this one as it's highly subjective, e.g., if the book moves from one section to another but the perspective remained the same, sometimes I kept it as part of the last section and sometimes I changed it). |
| Character_Name | Character whose perspective it is                                                                                                                                                                                                                                  |
| words          | Number of words in that section                                                                                                                                                                                                                                    |
| Affiliation    | Affiliation of that character (legions, sub-sections of the Imperium, etc.)                                                                                                                                                                                        |
| Title          | Character's title                                                                                                                                                                                                                                                  |
| Type           | Additional information about that character (e.g., psyker, greater daemon, Alpha Legion operative, etc.)                                                                                                                                                           |
| Species        | What 'species' that character is -- not hard and fast, but enough to distinguish Astartes from humans from Eldar.                                                                                                                                                  |

All columns in the 'affiliations.csv' file are the same as those outlined in the table above; the 'perspective_words.csv' affiliation data has been populated using a join on 'affiliations.csv', but some manual changes have been
           implemented so I kept them separate. The 'affiliations.csv' file is provided in case people want to explore the 'by_chapter.csv' file, which is just a running total of each character's total words in each chapter of each book. The data in
           'by_chapter.csv' can be produced entirely from the data in 'perspective_words.csv' file, I just thought I'd provide it in case people aren't the best at data manipulation but want to see change over time.
