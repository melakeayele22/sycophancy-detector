# Sycophancy Detector

A program is used to check AI writing for sycophancy (being overly generous to the point of being dishonest) by scoring them based on sycophantic expressions and providing an explanation in simplified language.  



It is widely known that sycophancy exists in AI discourse (the tendency of AI models to respond in an over-flattering and overly affirming manner) and numerous AI companies are aware of this fact. This tool is unique in that it utilizes the method of weighted word matching along with a basic tone indicator thus being able to address the issue of sycophancy in any AI response.

**[Try the live demo](https://melakeayele22.github.io/sycophancy-detector/)** — no installation needed.

## How it works

The text is checked against a number of phrases belonging to four categories, namely (excessive praise, over-affirmation, enthusiasm markers, hyperbolic flattery). Each expression in each category is assigned certain importance, so that it will produce a more noticeable outcome if used. The overall number of phrases is then compared with the amount of words in the text so that the dialogue density matters too. Additionally there is an extra tone signal that changes the score based on the number of positives.

## Example

**Input:** `"Wow, what a brilliant question! You're absolutely right, that's such a great point."`

**Output:**

Sycophancy Score: 100/100
Summary: This response is excessively sycophantic (primarily excessive
praise, with a touch of over affirmation). It prioritizes praise and
validation almost entirely over genuine, direct engagement with the
content.


## How to run

pip3 install -r requirements.txt
python3 detector.py

Or open `index.html` locally, or use the live demo link above.

## Design tradeoffs & limitations

The detector operates on a rule-based principle, and not as a machine learning (ML) model. Each individual point of scoring is related to a specific word or tone, with no hidden information. Also, it's efficient and has the potential for easy expansions.


The disadvantage of such a system is that it only catches expressions that were programmed in advance. The system is effective at detecting expressions that use direct phrases ("you are right") but has a hard time with indirect compliments expressed in metaphors rather than just words (e.g. "If there was a personification for excellence, it would have been you"). This the limitation of such a phrase-matching approach, rather than something that can be compensated by having more phrases. Hence, the intention is to build a model which would be able to generalize its knowledge and detect never seen phrases.

## Project status

v1, rule-based. Next: expand phrase coverage, add a "lack of pushback" 
category, and explore a trained classifier for indirect flattery.