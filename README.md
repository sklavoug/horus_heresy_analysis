# 0 - Intro

I'm not a great painter and I don't think I've ever won a game of 40k, but I'm a data analyst and I absolutely loved the series. I was up to about book 4 when I realised that the series itself was long enough and granular enough to be a dataset. Bought all the ebooks as I was reading them and essentially tagged each section with characters' perspectives; this exercise is pretty trivial for other series like Wheel of Time or A Song of Ice and Fire because chapters are named after their characters' perspective, but here's the Horus Heresy changing perspectives multiple times in each chapter, and on a few occasions, in a single sentence (looking at you Dan Abnett).

What I'm left with is 7,180 instances of perspectives for 739 characters total. Worth mentioning this is *all* characters, including ones whose perspective lasts a few words until they're squished by a Space Marine (or, in one very specific instance, from a knife's perspective). The dataset is open and available in the 'data' folder. Hopefully there's no copyright issues here, I've only released book and character names/affiliations which is less information than the wiki pages have (see the appendix for more detail on what's included in each of the csv files).

Final note: I've included short stories in this analysis; there's an argument for excluding them since they can skew a few of the results, but a) they are an important part of the narrative, b) they're often used to bridge certain events together meaning characters often appear in short stories as well as longer books, and c) some of them absolutely slap so worth keeping in.

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

I've loosely classified the 'species' of each perspective in Table 1a; species probably isn't the right word, but it's enough to show the difference between humans, Astartes, and Primarchs. Unsurprisingly the Astartes lead with just over 50% of the total perspectives, and a whopping 3.9 million words total. Humans are half that at 1.8 million, but for reference, that means the total human perspectives in the Horus Heresy are as long as ASOIAF. Primarchs have a good showing at just over a million words, and down the bottom we have interesting segments like 'Progenitor', 'Lacrymole', and 'Tyranids'. Oh, and 'Knife'; yes there is a section of this series that's from the perspective of a knife.

# 2 - Characters

The top character is Loken with 217,993 words, around 2.91% of total words in the series. For reference, Loken's perspective takes up approximately 1.86 books based on average length per book.

**Figure 2a. Top 10 characters by total words**
![A bar chart showing the top 10 characters by word count. The top is Loken, followed by Zahariel, Garro, Ahzek Ahriman, Sanguinius, Abaddon, Corvus Corax, Vulkan, Kasper Hawser, and Oll Persson.](https://github.com/sklavoug/horus_heresy_analysis/blob/main/2a%20-%20Top%2010%20Chars.png?raw=true)

Interestingly, the top 10 characters by total words (Figure 2a) is quite diverse. There are 5 Astartes, 3 Primarchs, a Perpetual, and a random human. This doesn't *quite* align with the overall stats by species (see Table 1a), but it's correct on Astartes at least. The top words are only part of the story part of the story for characters, however. If we look at the same characters by words per book, a different picture emerges.

In terms of who's in the top 10, there's quite a diversity in terms of what kinds of characters/perspectives they have. Case in point: Loken is important in the first 3 books and the last 7ish, but doesn't really feature all that much in any other book. In contrast, Zahariel does a lot of heavy lifting for the Dark Angels and has a lot of books in which he's the majority perspective. With that in mind, let's keep these top 10 characters, but see their average words per book.

**Figure 2b. Top 10 Chars (Most Words) by Avg Words per Book**
![A bar chart showing the top 10 characters by word count, by average words per book. Kasper Hawser is almost 3 times as prominent as the next highest, Corvus Corax.](https://github.com/sklavoug/horus_heresy_analysis/blob/main/2b%20-%20Top%2010%20Chars%20(Most%20Words)%20by%20Avg%20Words%20per%20Book.png?raw=true)

In this case, we can see Kasper Hawser is almost 3 times further ahead than the next character. This makes a lot of sense -- Kasper Hawser basically has his own book in which he is really the only perspective, whereas even Loken -- who has the most words in the entire series -- is spread across quite a few books. Notably this is the top 10 by total words; let's see what it looks like when we use words per book as the metric to decide the top 10.

**Figure 2c. Top 10 Chars (Avg Words) by Avg Words per Book**
![alt text](https://github.com/sklavoug/horus_heresy_analysis/blob/main/2c%20-%20Top%2010%20Chars%20(Avg%20Words)%20by%20Avg%20Words%20per%20Book.png?raw=true)

Uh, ok. This is...interesting. I know Kasper Hawser, Kai Zulane, and Archamus. But uh...who are the rest of these people? Anton Galba? Dalia Cythera was in 'Mechanicum' I'm pretty sure. Dravian Klayde? Corvus Corax? Oh wait I do know him. Pretty sure Lysimachus is an Imperial Fist? Meros is the Blood Angel madlad, and Zenobi is the true Arch-Traitor. This is an interesting dynamic, as while I know exactly who the top 10 are by total words, I have to really think about the top 10 by average words per book. Kasper Hawser has more words per book than any other character, but he's only in one book: his perspective is *focused*. But in a series with 64 books, characters who appear in multiple books tend to have more impact, since they're just present at more events (e.g., the Long Companions, Erebus, etc.).

There's one other aspect to this that relates closely to avg words per book, and that's average *proportion* of book this character occupies. This one's going to be a bit different since we're getting away from total words, and taking averages of percentages is a bit weird (e.g., they might have 10,000 words in a really long book and make up 1% and 10 words in a super short book and make up 10%), but it's more a check of the breadth of their perspective.

**Figure 2d. Top 10 Chars by Proportion of Book (character name and book number)**
![alt text](https://github.com/sklavoug/horus_heresy_analysis/blob/main/2d%20-%20Top%2010%20Chars%20by%20Proportion%20of%20Book.png?raw=true)

Now we're back in familiar territory; interestingly 8 of the top 10 characters by total words make up the top 10 by proportion of book, with Zahariel and Garro featuring twice for 2 books. This is interesting as there's not necessarily a relationship between total words and proportion of words in book; Oll Persson is a good example of this, as he's in the top 10 total words but only appears on the list of proportion of book at number 57 with 19.5%. What this demonstrates is that most of the top 10 by words tend to have at least one book centred on them.

Let's wrap up characters with a look at avg length of perspective vs number of books the character has appeared in. This gives me a chance to make a quadrant graph (yay!) and label each of the quadrants. Our top right is going to be 'Protagonists': these are characters with long perspectives and frequent appearances, they're the real mainline perspectives throughout the series. Bottom right is 'Lore Dump': these are characters with long perspectives and infrequent appearances, so they more act as one-and-done insights into particular areas (like Kasper Hawser for the Space Wolves, or Dalia Cythera for the Mechanicum). Bottom left is 'Incidental', which is most of the characters: short perspectives and infrequent appearances. I'm going to set a threshold for featuring on this chart, because otherwise it'll just be a bunch of circles in the bottom left. And finally, in the top left quadrant will be 'Hand of Destiny': short perspectives and frequent appearances. The main one I'm thinking of here is Erebus (duh), because this category is for characters who we aren't necessarily following through the series (like the Protagonists), but for characters who are subtly or unsubtly making an impact on events at key points. Did I just want to make this graph so I could label one of the quadrants 'Hand of Destiny'? Yes, absolutely.

**Figure 2e. Characters by Avg Words and Books**
![alt text](https://github.com/sklavoug/horus_heresy_analysis/blob/main/2e%20-%20Characters%20by%20Avg%20Words%20and%20Books.png?raw=true)

Interesting, another unexpected result! The Protagonists are pretty sparse: just Sanguinius, Abaddon (???) and Loken. Loken and Sanguinius I get, they both have a lot of perspectives, but Abaddon is an interesting one; although I guess he features a lot in the back end? Regardless, the lore dumps in the bottom right are also about right: Zahariel, Ahriman, Garro, and Corax; one member of each of the less-explored Legions, although Zahariel did appear in 7 books overall (I think he's more protagonist but might have been undermined by a few short stories). Bottom left isn't worth going into, although there are a few Primarchs in there. And finally, the Hand of Destiny, which is honestly more crowded than I thought it would be. John Grammaticus and Oll Persson are both in there which makes sense (John slightly higher which kinda reflects that he's doing more actual influencing than Oll), Sigismund (makes sense), Erebus (duh, it's named after him), Malcador and Rogal Dorn (yup definitely, a lot of books feature them on Terra staring pensively at the sky), and Horus! The big H himself is in the Hand of Destiny category, which honestly makes perfect sense: he has a lot of snippets at the end of books where he broods, and is bumped up in words by the opening trilogy and final arc.

Well that about wraps up the characters, it's on to part 3: the Legions!

 # 3. Legions
Although the series features characters from all sorts of backgrounds, species, and affiliations, it's absolutely a story about the Astartes. The Space Marines occupy just over 50% of the series with their perspectives, although if you include the Primarchs they're over 2/3rds of the series (as seen in Table 1a). Each of the Astartes (barring one character) are descended from one of 18 Legions, which aren't necessarily equally represented.

**Figure 3a. Sum of words by Legion**
![alt text](https://github.com/sklavoug/horus_heresy_analysis/blob/main/3a%20-%20Sum%20of%20words%20by%20Legion.png?raw=true)

Figure 3a shows the sum of words per Legion, with the Sons of Horus topping the list with over 500K, followed by the Dark Angels with 330K. This makes sense, but similarly to characters, the top 2 both have different roads to the podium. The Sons of Horus are at the top similarly to how Loken is: they're really prominent at the beginning and end, but unlike Loken, they feature quite a bit in the middle as well -- either at the beginning/end of books, as villains for the 'protagonist' legion, or with their own standalone book/short stories. In contrast, the Dark Angels walk the spiral mostly with Zahariel, who just dominates every book he's in. They also have 2 or 3 books devoted to them in the first 15, and further in we get more of the Caliban perspectives so they double dip a bit. The Ultramarines are also high in the rankings and a solid third, but I'll cover them in Figure 3b.

In contrast to the top, without a doubt, the lowest 2 are the Night Lords (81K) and Alpha Legion (54K). It's worth noting here that the Alpha Legion makes sense as we rarely actually see their perspective, and interact far more with their human agents or Alpharius/Omegon; it's similar for the Night Lords, as the majority of their story is told via Konrad Curze himself. If you include non-Astartes characters (i.e., Primarchs and humans) for these factions, their totals increase to 171K for the Alpha Legion and 99K for the Night Lords.

Before we proceed further, a quick note on methodology. I said above that the Astartes are 'descended' from one of the 18 Legions; this is very deliberate wording, as saying they're 'members' of a Legion would make it tricky to define characters like Loken and Garro, who forsake their Legion and actively fight against them. The Knights-Errant create a bit of an issue when trying to straighten out this dataset, as they a) feature quite prominently, and b) are prevalent enough that they do change the figures for a few Legions overall (just remember how much Loken content is in the Siege of Terra). In the end I've included them in most analysis for their parent Legion, which is for a couple of reasons. The first is the idea that they are 'biologically' a part of that Legion, in that they have their primarch's gene-seed whether they like it or not. If there were a virus that only targeted Mortarion's DNA, then Garro would be caught up in it just like the rest of the Death Guard (although he'd probably be the only one affected since the DG are already pretty messed up biologically). As well, from a narrative perspective, these characters' sections do deal a lot with what it means to stand apart from one's Legion. Loken with the Sons of Horus, Garro with the Death Guard, and Tylos Rubio with the Ultramarines: they're all off doing Sigillite-y things, but a lot of their sections involves them thinking about and grappling with their Legion and their history. If they renounced their Legion and then just never thought about them again, it'd be harder to argue that they should still be included in those Legions' results. But from the core idea that a Legion's perspective represents their prevalence in the Heresy, and how much the Heresy is their story, then the Knights-Errant still fit with their original Legions.

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

Last one on the Legions, let's look at chapters per book per Legion, since I think this will show the SoH dropping down as they're more tangential.

**3c. Average chapters per book by legion (excl short stories)**
![alt text](https://github.com/sklavoug/horus_heresy_analysis/blob/main/3c%20-%20Avg%20Chapters%20per%20Book%20by%20Legion.png?raw=true)
From Figure 3c we can see that the Salamanders and Thousand Sons are the top Legions in terms of chapters per book, at over 20 chapters on average each -- makes sense since the Thousand Sons and Salamanders tend to be the sole participants of books they're in. The next 3 are the Iron Hands, Ultramarines, and Sons of Horus, which does make sense as they tend to be protagonists in a few books but feature in a lot of others. This metric also isn't perfect -- most notably it's dependent on how many chapters a book has, and there's definitely a Salamanders book with 60 chapters in there somewhere which would skew their average. But it presents a different way to view the data and shake up the rankings, as the Sons of Horus are in 5th place here, and notably, the bottom 2 in this chart are the Space Wolves and World Eaters (as opposed to the Night Lords and Alpha Legion, who are still low but not at the very bottom here).

So yeah, I guess that about wraps up my analysis. Not much else to talk about here, just characters and Legions...nah just kidding, let's get to what you're really here for: the Primarchs!

# 4. The Primarchs ###

There's a lot that can be done with the Primarchs because they kind of form the most consistent subset of the data. What does that mean? Well for characters, they obviously vary wildly in terms of total words. Similarly for the Legions, we can see there's a lot of diversity in the results based on how prominent they are. But there's more foundational elements there, e.g., does one Legion have more characters featured than another? And then we have to try and flatten that out by averaging chapters per book per Legion. But with the Primarchs, there's exactly 18 of them, so there's less scope for differences in characters *within* a subset to change the result. With all that aside, for those of you who didn't make the connection in the first section where we looked at the characters overall, let's dig in and see who's most prominent!

**4a. Primarchs by Words**
![alt text](https://github.com/sklavoug/horus_heresy_analysis/blob/main/4a%20-%20Primarchs%20by%20Words.png?raw=true)

And there it is, Sanguinius is undoubtedly the most prominent Primarch in the Heresy -- and eagle-eyed readers would've seen that since he, Corax, and Vulkan are the top 3 Primarchs and all feature in the top 10 characters overall in the series. The next-highest is Horus, who does get a boost in the final books (I've counted the second-person sections as being from Horus' perspective since they basically are), and then there's a bit of a gap until we reach the middling numbers where the majority of primarchs sit. It's interesting to look at the least-prominent Primarchs: Angron, Ferrus Manus, Konrad Curze, and Magnus. This is in contrast to the previous section where we looked at their legions; Konrad Curze is the throughline here since he and his Legion are both quite low in terms of representation, but Alpharius is more in the bottom middle here with 40K words, whereas the Alpha Legion overall were in the bottom 2. Similarly, the Iron Hands and Thousand Sons were higher up the rankings in terms of overall perspectives, even though their primarchs have a relative dearth of perspectives. This again comes down to writing style of each author and structure of each book, since some Legions have a lot of their Primarch's perspective and others have relatively little.

There's another interesting thing here, and it's that some of the Primarchs' amounts are actually high enough to make a change in the Legion rankings. The Raven Guard and Blood Angels were both towards the bottom in terms of the Legion rankings with around 150K each, but we can see here that their Primarchs add around 150-200K words themselves to those rankings. So let's re-adjust the Legion rankings, but this time including Primarchs.

**4b. Legions (including Primarchs) total words**
![alt text](https://github.com/sklavoug/horus_heresy_analysis/blob/main/4b%20-%20Legions%20(inc%20Primarchs)%20total%20words.png?raw=true)Hmm, interestingly it doesn't actually make much of a difference. Seems even when you include the Primarchs a high tide raises all ships, because it kinda looks the same as before. Oh well, that's what happens with data -- don't know what you're gonna find until you get into it. But what's good about that is it's given me a further idea, to look at what proportion of their Legion's total perspective the Primarch makes up. Again, it's imperfect but it's a way of reframing the data to look at interactions within it rather than just looking at total words etc.

**4c. Primarch proportion of words per Legion**
![alt text](https://github.com/sklavoug/horus_heresy_analysis/blob/main/4c%20-%20Primarch%20proportion%20of%20words%20per%20Legion.png?raw=true)

Interestingly, looking at Primarchs as a proportion of the Legion overall definitely shows a difference. The Alpha Legion, Blood Angels and Raven Guard have over 40% of their perspectives from their primarch -- makes sense for AL since there's so little of their perspective, and Corax and Sanguinius are both pretty high in total words. Interestingly too, the lowest (sub 10%) are the Iron Hands and the Thousand Sons -- again, makes sense but for different reasons, as Ferrus Manus dies early in the Heresy and most of the IH perspectives are the Shattered Legions, and Ahriman does most of the talking for the T Sons.

# 5. Conclusion

And that's it! Tbh I burned out a little bit on doing this so haven't gone much further than the descriptive stuff for the Legions, and didn't get wild with some of the visualisations. Originally I'd hoped to do a full scrollytelling (data storytelling but it changes as the user scrolls through) thing for this but it was way too much work and I was trying to prioritise people getting their hands on the data so they could take a look themselves. The main thing I'm interested in in the future is looking at words spoken by each character, but that's a whole different and more complicated exercise that would probably require some machine learning (although good excuse to practice with LLMs).

Hope you enjoyed! Like I said, data's free and open so feel free to jump in and have a look. I've also included the script that generated this markdown file ('horus_heresy_analysis.py'), including all tables and visualisations -- it's not my best coding and there's a lot of duplication of variables, but at the very least it'll give people a head start if they're not sure where to jump in.

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

**How was this data collected?**
All ebooks for the Horus Heresy were purchased legally -- I used Calibre to read through them, and manually copied and pasted the opening and closing block (e.g., sentence or sequence of words) into a csv file along with the name of the character whose perspective it was. This was then fed to a Python script that ran through the relevant ebook and chapter, pulled out the relevant section (i.e., what was between the start and end strings), and counted the words in it. This was then output and joined with affiliations.csv to create the final perspective_words.csv file.
