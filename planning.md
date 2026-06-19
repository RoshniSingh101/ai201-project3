# Evaluation Plan

## Community
What community did you choose and why? Why is this community a good fit for a classification task — what makes the discourse varied enough to be interesting?
```
I chose r/LetsTalkMusic because my FYP on TikTok always houses music content, so I have some background on what's been going on in pop culture recently. The community has strong opinions, discussion posts, and questions users pose that varies across several genres. As a result, we get a diverse dataset from pop and R&B to rap and country music. 
```

## Labels
What are your 2–4 labels? Define each in a complete sentence. Include 2 example posts per label.
```
"opinion": "the post leads with a topic that they have seen a lot of on social media and proceed to explain how they feel about the topic"
- Example #1: "Olivia Rodrigo's New Album" u/SxnKisss talks about how they say lots of praise for her new album "you seem pretty sad for a girl so in love" and how they do not understand why more people are not critiquing it. 
- Example #2: u/thirdaccounttt has a post called "Lyrics are massively overvalued in how people judge music" and shares their opinion how there is more to judging music that lyrics alone

"discussion": "users will mention they want to talk about a band, single, artist, or song in their title to open the floor to hear what others have to say"
- Example #1: u/wildistherewind "Let's Talk: Saturday Night Fever, The Bee Gees, and Disco Demolition Night" opens a discussion thread discussing hit singles from these groups and how they were ranked for top singles of the year
- Example #2: u/slinkenboog "Alright everybody-please break down Deftones for me." opens discussion on how they should feel about an artist

"question": "ask questions about how others feels about new single and album releases or advice on curating playlists"
- Example #1: u/grovelor posted "Why is an artist's music often perceieved as 'cheapened' by having a predominantly teenage female fanbase?" asking why artists are disrespected more when teenage girls enjoy the music
- Example #2: u/Human_Addendum4427 "Why Do People Act Like Their Opinion on Music Is A Fact?" asks why people feel entitled to treating their opinions on music as a fact
```

## Hard edge cases
What type of post will be genuinely ambiguous between two labels? How will you handle it when you encounter it during annotation?
```
u/jberg08 posed a question post "How music was before" but there is no question mark at the end that may mistake the post as a discussion one. To fix the issue, check if the end of a title post has a question mark. If it does not, check if the title starts with how, why, when, who, what, or where to label it as a question post.

u/SandmanAlcatraz "Never Mind the Bollocks, Here's the Sex Pistols" can be an opinion or discussion post at first glance. I would classify this as an opinion post because the post itself does not open discussion to other opinions, but the user shares their own as a standalone post. Key words such as "I feel like", "I think", "I believe" or I statements would differentiate it as an opinion post. "What do you think?", "what others think," "would you agree" any you statements would identify the post as a discussion post. 
```

## Data collection plan
Where will you collect examples? How many per label? What will you do if a label is underrepresented after 200 examples?

```
Reddit is where the examples will come from under the subreddit r/LetsTalkMusic. If a label is underrepresented, I will add 100 more examples for that label. 
```

## Evaluation metrics
Which metrics will you use to evaluate your model and why are those the right ones for this specific task? (Accuracy alone is not enough — explain what else you need and why.)
```
We need to test for accuracy, precision, and recall. Accuracy is the percentage of total label predictions the fine-tuned model got, precision measures the number of true positive labels the model receives, and recall accounts for the percentage of resutls that were relevant (i.e. related to music, artists, songs, associated genres, bands etc).
```

## Definition of success
What performance would make this classifier genuinely useful? What would you accept as "good enough" for deployment in a real community tool?
```
As a minimum viable product, I would accept 85% performance accuracy and 90% as good enough for deployment. In future models, I would shoot for 95%. 
```


## AI Tool Plan

### Label stress-testing
Give the AI your label definitions and edge case description, and ask it to generate 5–10 posts that sit at the boundary between two labels. If it produces posts you can't classify cleanly, your definitions need tightening — do that now, before you annotate 200 examples.
```
Opinion ↔ Discussion

Phoebe Bridgers is the most overrated artist of the last decade, and I'm tired of pretending otherwise
u/coldtakeking
Every time I open this subreddit she's being praised like she invented sadness. The guitar work is fine, the lyrics are fine — none of it moves me. I know this is going to be controversial but I've felt this way for years.
Tension: Leads with a personal opinion and uses "I" throughout — but the provocative framing ("I know this is controversial") implicitly invites a debate. No "what do you think?" but the post clearly expects a reaction. Does implicit audience-baiting count as opening a discussion?

Let's settle this: Rumours is the greatest album ever made
u/fleetwoodmaximum
I know "greatest ever" is a hot take but I've been listening for 30 years and nothing touches it. The production, the songwriting, the emotional rawness — it all holds up. Curious if anyone actually disagrees.
Tension: "Let's settle this" is a discussion opener, but the body is pure first-person opinion with no question posed until the final throwaway line. Your rule says key phrase "curious if anyone disagrees" functions as a "you statement" — but is a single sentence at the end enough to flip the label?

Opinion ↔ Question

Why does every indie artist sound exactly the same now
u/noisepopnostalgia
VSCO aesthetics, bedroom pop vocals, the same four chords. I feel like the genre has completely collapsed into itself and no one is pointing it out. It's frustrating to watch something I loved become a template.
Tension: Starts with "why" (your question heuristic) but has no question mark and the body is entirely first-person complaint — no genuine inquiry into others' views. Applies your edge-case rule about "How music was before" but in reverse: the "why" is rhetorical, not a real question.

Am I the only one who thinks Beyoncé's country era is her strongest work?
u/Renaissancerepeat
I've been saying this since Cowboy Carter dropped. The songwriting is sharper, the production risks are bigger, and she sounds more free than she has in years. I genuinely think it's her peak and I can't find anyone who agrees.
Tension: Starts with "am I the only one" — a question structure — but the post is a fully formed opinion with no actual request for information or advice. The question is rhetorical. Does a rhetorical question in the title satisfy your question label criteria?

Question ↔ Discussion

What makes a song "timeless" — genuinely asking
u/halfspeedlistener
Not looking for a definitive answer, just want to hear how people think about it. Is it production that doesn't date? Lyrics that stay universal? I keep coming back to this question every time I hear something 40 years old that still slaps.
Tension: Has a question mark and starts with "what" — fits your question heuristic — but the body explicitly says "I want to hear how people think about it," which is a discussion opener. It's asking for process/reflection rather than factual advice. Does the explicit invitation to share perspectives push it to discussion?

Breaking down Charli XCX for someone who's never listened: where do I start?
u/hyperpopvirgin
My friend keeps sending me her stuff and I don't know how to feel about it yet. Is there an obvious entry point, or do I just jump into BRAT? Would love to hear from people who were also late to her.
Tension: Asking for playlist/entry-point advice (fits your question definition), but "I'd love to hear from people who were also late to her" opens the floor for personal stories — closer to discussion. Compare to your example of u/slinkenboog asking for a Deftones breakdown: nearly identical structure. Which label did you use there?
```

### Annotation assistance
Decide whether you'll use an LLM to pre-label a batch of examples before reviewing them yourself. If yes, note which tool you'll use and how you'll track which examples were pre-labeled (for disclosure in your AI usage section).
```
I will use LLM to pre-label posts from the r/LetsTalkMusic thread.

206 rows total — 64 opinion, 65 discussion, 77 question — with 9 rows flagged with notes covering the edge cases from the plan
```

### Failure analysis
Plan to give your list of wrong predictions to an AI tool and ask it to identify patterns before you write up your evaluation. Note what you'll look for and how you'll verify the patterns yourself.
```
I will use a training set of 10 posts without labels before training the model to see how it labels the posts based on my label descriptions.
```

## Milestone 4 - Baseline

```
🎯 Baseline accuracy: 1.000  (evaluated on 31/31 parseable responses)

Per-class metrics (baseline):
              precision    recall  f1-score   support

     opinion       1.00      1.00      1.00        10
  discussion       1.00      1.00      1.00        10
    question       1.00      1.00      1.00        11

    accuracy                           1.00        31
   macro avg       1.00      1.00      1.00        31
weighted avg       1.00      1.00      1.00        31

```

Reflection: The baseline was perfect. No struggles encountered. 

## Milestone 5 - Fine-Tuning

```
🎯 Fine-tuned model accuracy: 0.903

Per-class metrics (fine-tuned model):
              precision    recall  f1-score   support

     opinion       1.00      1.00      1.00        10
  discussion       0.89      0.80      0.84        10
    question       0.83      0.91      0.87        11

    accuracy                           0.90        31
   macro avg       0.91      0.90      0.90        31
weighted avg       0.91      0.90      0.90        31
```

### Confusion Matrix
![confusion matrix](confusion_matrix.png)

### Wrong Predictions

```
Wrong predictions: 3 / 31

--- #1 ---
Text:      What is the most influential album that most people have never actually listened to?
True:      question
Predicted: discussion  (confidence: 0.35)

--- #2 ---
Text:      Thoughts on Lil Wayne's peak era? Is he underrated in the GOAT conversation because he's hard to fit into a narrative?
True:      discussion
Predicted: question  (confidence: 0.34)

--- #3 ---
Text:      Can we talk about how music documentaries shape legacy? Are they revealing or are they canonizing?
True:      discussion
Predicted: question  (confidence: 0.35)
```