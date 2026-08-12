# Sycophancy Detector

A Python tool that scores AI-generated text for sycophantic language — 
excessive praise, over-affirmation, hyperbolic flattery, and enthusiasm 
markers — and explains *why* it scored the way it did in plain language.

Sycophancy in AI models (over-flattering, over-agreeing responses that 
prioritize validation over honesty) is a well-documented issue across 
major AI labs. This tool combines weighted phrase matching with a 
lightweight tone signal to flag and quantify that behavior in any given 
AI response.

**[Try the live demo](https://melakeayele22.github.io/sycophancy-detector/)** — no installation needed.

## How it works

Text is checked against a set of sycophantic phrases across four 
categories (excessive praise, over-affirmation, enthusiasm markers, 
hyperbolic flattery), each phrase individually weighted by how strong a 
signal it is. Matches are normalized against the response's word count, 
so density matters more than raw count. A secondary tone signal adds a 
small boost for strongly positive language even without an exact phrase 
match. The result is a 0–100 score with a plain-language summary.

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

This detector is intentionally rule-based rather than a trained ML 
model — every point of the score traces back to a specific phrase or 
tone signal, with no black-box reasoning, and it's fast and easy to 
extend.

The tradeoff: it only catches what it's explicitly been told to look 
for. It performs well on direct phrasing ("you're absolutely right") but 
struggles with **indirect flattery** conveyed through metaphor rather 
than a literal phrase, e.g. *"if excellence were a person, it would be 
you."* This is a structural limitation of phrase matching, not something 
more phrases alone can fully close — which is why a trained classifier, 
generalizing to unseen phrasing, is the planned v2.

## Project status

v1, rule-based. Next: expand phrase coverage, add a "lack of pushback" 
category, and explore a trained classifier for indirect flattery.