### News

* **28th May 2018:** The **development dataset** is now available for [download](https://github.com/nlp4fun/nlp4fun.github.io/blob/master/data/training/nlp4fun_train_v1.xml).
* **28th May 2018:** [Task guidelines](https://github.com/nlp4fun/nlp4fun.github.io/blob/master/guidelines/nlp4fun-evalita-2018-guidelines-v100.pdf) are now available.
* **3rd April 2018:** Registration are now open! Fill-in the [form](https://docs.google.com/forms/d/e/1FAIpQLSdAKar1gv-Spoc3cPGYyzgBG5-fETVWvKfvSO1_v-Wc6RNfjQ/viewform).

### Menu
* [Task Description](#task-description)
* [Data Description](#data-description)
* [Data Format](#data-format)
* [How to Participate](#how-to-participate)
* [Important Dates](#important-dates)
* [Organizers](#organizers)
* [Contacts](#contacts)

### Task Description
Language games draw their challenge and excitement from the richness and ambiguity of natural language, and therefore have attracted the attention of researchers in the fields of Artificial Intelligence and Natural Language Processing.
For instance, IBM WatsonTM is a system which successfully challenged human champions of Jeopardy!TM, a game in which contestants are presented with clues in the form of answers, and must phrase their responses in the form of a question [[1]](#1). Other researchers exploited question answering techniques to build an artificial player for _“Who Wants to be a Millionaire?”_ [[2]](#2). Another popular language game is solving crossword puzzles. The first experience reported in the literature is Proverb [[3]](#3), that exploits large libraries of clues and solutions to past crossword puzzles. WebCrow is the first solver for Italian crosswords [[4]](#4).

The proposed task consists in designing a solver for **“The Guillotine” (La Ghigliottina, in Italian)** game. It is inspired by the final game of an Italian TV show called “L’eredità”. The game, broadcast by Italian National TV, involves a single player, who is given a set of five words - the clues - each linked in some way to a specific word that represents the unique solution of the game. Words are unrelated to each other, but each of them has a hidden association with the solution. Once the clues are given, the player has one minute to find the solution. For example, given the five clues: _sin_, _Newton_, _doctor_, _New York_, _bad_, the solution is **apple**, because: the apple is the symbol of original sin in Christian theology; Newton discovered the gravity by means of an apple; _“an apple a day keeps the doctor away”_ is a famous proverb; New York city is also called _“the big apple”_; and _“one bad apple can spoil the whole bunch”_ is a popular phrase which figuratively means that the person doing wrong can have a negative influence on those around him. “La Ghigliottina” is a challenging language game which demands knowledge covering a broad range of topics. Artificial players for that game can take advantage from the availability of open repositories on the web, such as Wikipedia, that provide the system with the cultural and linguistic background needed to understand clues [[5]](#5).
Participants must build an artificial player able to solve “La Ghigliottina”.

### Data Description

### Data Format
We will provide a set of both training and testing games in the XML format:
```xml
<games>
  <game>
        <id>3fc953bd-bd48-4fb9-a86c-bd979c1b5c3f</id>
        <clue>uomo</clue>
        <clue>cane</clue>
        <clue>musica</clue>
        <clue>casa</clue>
        <clue>pietra</clue>
        <solution>chiesa</solution>
  </game>
  …
</games>
```

The XML file consists of a root element *games* which contains several *game* elements. Each game has five *clue* elements and one *solution*.
The games have been collected by the organizers from both the TV show and the board game. The current dataset contains 421 games. We will provide 316 and 105 games as training and testing, respectively. The participants can integrate any knowledge resources in their systems except further games.

Participants must provide for each game a ranked list of maximum 100 tentative solutions. Results must be provided in a text plain file according to the following format:

> id solution score rank time

Values must be separated by a whitespace character and time must be reported in milliseconds. For example:

> 3fc953bd-bd48-4fb9-a86c-bd979c1b5c3f porta 0.978 1 3459<br>
3fc953bd-bd48-4fb9-a86c-bd979c1b5c3f chiesa 0.932 2 3251<br>
3fc953bd-bd48-4fb9-a86c-bd979c1b5c3f santo 0.897 3 4321<br>
...<br>
3fc953bd-bd48-4fb9-a86c-bd979c1b5c3f carta 0.321 100 2343<br>

As evaluation measure, we adopt a weighted version of Mean Reciprocal Rank (MRR). Since time is a critical factor in this game, the Reciprocal Rank will be weighted by a function which takes into account the time. In the TV game, the player has one minute to provide the solution. Taking into account these factors, the final evaluation measure is:

<img src="https://latex.codecogs.com/gif.latex?\frac{1}{\left&space;|&space;G&space;\right&space;|}&space;\sum_{g&space;\in&space;G}&space;\frac{1}{r_{g}}&space;max&space;\left&space;(&space;\frac{1}{t_{g}},\frac{1}{10}&space;\right&space;)" title="\frac{1}{\left | G \right |} \sum_{g \in G} \frac{1}{r_{g}} max \left ( \frac{1}{t_{g}},\frac{1}{10} \right )" />

where *G* is the set of games and *r<sub>g</sub>* is the rank of the solution, while *t<sub>g</sub>* denotes the minutes taken by the system to produce the tentative solutions. Systems that take more than 10 minutes are equally penalized.

### How to Participate

Online registration is open: [registration form](https://docs.google.com/forms/d/e/1FAIpQLSdAKar1gv-Spoc3cPGYyzgBG5-fETVWvKfvSO1_v-Wc6RNfjQ/viewform).

### Important Dates
*(tentative)*

* **28th May 2018:** development data available to participants
* **10th September 2018:** test data available, registration closes
* **10th - 16th September 2018:** evaluation window (system results due to task organizers)
* **24th September 2018:** assessment returned to participants
* **5th November 2018 (tentative):** technical reports due to organizers (camera ready)
* **12th or 13th December 2018:** final workshop

Further details will be made available in the near future.

### References
[<a name="1">1</a>] D. Ferrucci, E. Brown, J. Chu-Carroll, J. Fan, D. Gondek, A. A. Kalyanpur, A. Lally, J. W. Murdock, E. Nyberg, J. Prager, N. Schlaefer, and C.Welty, “Building Watson: An overview of the DeepQA project,” AI Magazine, vol. 31, no. 3, pp. 59–79, 2010.

[<a name="2">2</a>] P. Molino, P. Lops, G. Semeraro, M. de Gemmis, and P. Basile. Playing with knowledge: A virtual player for who wants to be a millionaire? that leverages question answering techniques. Artificial Intelligence, vol. 222, pp. 157-181, 2015.

[<a name="3">3</a>] M. L. Littman, G. A. Keim, and N. Shazeer, “A probabilistic approach to solving crossword puzzles,” Artificial Intelligence, vol. 134, pp. 23–55, 2002.

[<a name="4">4</a>] M. Ernandes, G. Angelini, and M. Gori, “A web-based agent challenges human experts on crosswords,” AI Magazine, vol. 29, no. 1, pp. 77–90, 2008.

[<a name="5">5</a>] P. Basile, M. de Gemmis, P. Lops, and G. Semeraro, Solving a complex language game by using knowledge-based word associations discovery. IEEE Transactions on Computational Intelligence and AI in Games, vol. 8, no. 1, pp. 13-26, 2016.

---

### Organizers
* Pierpaolo Basile, Dipartimento di Informatica, Università degli Studi di Bari Aldo Moro
* Marco de Gemmis, Dipartimento di Informatica, Università degli Studi di Bari Aldo Moro
* Giovanni Semeraro, Dipartimento di Informatica, Università degli Studi di Bari Aldo Moro
* Lucia Siciliani, Dipartimento di Informatica, Università degli Studi di Bari Aldo Moro

### Contacts
If you have any questions, please contact us: <nlp4fun.evalita@gmail.com>.
