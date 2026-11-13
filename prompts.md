# Prompts — Thinking in HTML (Week 1 · Project 2)
- **Internship:** BSERC GenAI Internship · Week 1
- **Tool:** Claude (claude.ai)
- **Topic:** Grounded AI & ML foundations, built on my Project 1 notebook "GroundedAI"
  (sources: Dive into Deep Learning, Google ML Crash Course, Attention Is All You Need,
scikit-learn docs, PyTorch tutorials, my own notes)

Pages submitted:

- `1-ml-revision-dashboard.html` (Option: Revision or teaching dashboard)
- `2-classification-playground.html` (Option: Interactive 2D model)
- `3-grounded-answer-lab.html` (Option: My own idea)

## Prompt 1 — kick-off
[Attached the Week 1 Projects PDF]
"read this pdf fully and so till now i have done the notebooklm project and
project 2 i have to do now..ur task is based on my notebooklm project u have to
make good project whatever the project 2 says coz i have to submit it so yeah
make it good and here is the 1st project link <my notebook link>"

(Claude couldn't open the notebook link, because Google blocks automated
access, and asked me for my topic.)

## Prompt 2 — giving context
"alright i ll give u the context of my project: Grounded AI (or Source-Grounded
AI) refers to artificial intelligence systems engineered to generate answers,
analysis, and deliverables strictly anchored in verified reference sources ...
[full description of what Grounded AI does, its benefits, and my GroundedAI
notebook with its 8 reference materials: Dive into Deep Learning, Google's
Machine Learning Crash Course, Attention Is All You Need, scikit-learn
documentation, PyTorch tutorials ...]
read this and think of a new project related to this so that u can easily make
project 2 of that pdf"

## The three page prompts (4-part format: Who / What / Do / Rules)

### Page 1: ML Revision Dashboard
- **WHO:** Me, revising the ML topics from my GroundedAI notebook before an exam.
- **WHAT:** A study hub for AI vs ML vs DL, supervised/unsupervised learning, classical ML, deep learning, Transformers and grounded AI. Every item tagged with the notebook source it comes from, e.g. [3] = Attention Is All You Need.
- **DO:** Topic checklist with progress ring and per-group bars; exam countdown with date picker and daily pace; flip-cards with topic filter, search, status filter, shuffle, flip-all, and "knew it / review again" marks; 10-question scored quiz with explanations, skip, and a review screen; clickable source tags; dark-mode toggle; reset-all.
- **RULES:** One HTML file, no internet needed, works on a phone, facts must match the sources, save progress in the browser, check every button works.

### Page 2: Classification Playground
- **WHO:** A student learning how classifiers work (scikit-learn / ML Crash Course chapters).
- **WHAT:** A 2D plot where a classifier draws its decision boundary live, plus train vs test accuracy, precision, recall and a confusion matrix, so overfitting is visible.
- **DO:** Dataset switch (blobs, moons, circles, XOR); noise, point-count and test-split sliders; new-sample button; model switch (k-NN / logistic regression); k slider; linear vs polynomial features; learning-rate slider; animated training with a loss curve; +1 step; reset weights; click the plot to add points; undo; show/hide test points; confidence shading; an overfitting/underfitting message that updates.
- **RULES:** One HTML file, plain JavaScript (no libraries), works with touch on a phone, realistic sample data, explain each model in plain words with its source.

### Page 3: Grounded Answer Lab (my own idea)
- **WHO:** Classmates and teachers who want to SEE why source-grounded AI is more trustworthy than a chatbot answering from memory.
- **WHAT:** A mini "notebook" of short passages from my 6 source groups. You ask a question; it retrieves and ranks passages, answers only from them with clickable [1][2] citations, and says "Not in my sources" when the evidence is weak. Next to it, a simulated memory-only chatbot with planted mistakes to spot.
- **DO:** Question box + preset questions (including off-topic ones); Compare / Grounded / Memory mode switch; source on/off toggles; top-k slider; relevance-threshold slider; highlight-matched-words toggle; "spot the problems" button; clickable citations that jump to the evidence; a "claims with a citation" meter; reset.
- **RULES:** One HTML file, no internet, works on a phone. Passages must be my own short summaries (no copied text). Clearly label the memory answers as simulated.

## Fix rounds (found by testing every control on a laptop and a phone screen)
**Fix 1 (Page 2):** "The shaded background shows a visible grid pattern across the plot. Make the confidence shading smooth." → Field now drawn as a small image and scaled up smoothly.

**Fix 2 (Page 3):** "The off-topic question 'best learning rate for ResNet-50 on ImageNet' gets answered from a general learning-rate passage. A grounded assistant should notice the sources never mention ResNet or ImageNet and refuse." → Added a gap check: if key words in the question appear nowhere in the notebook, it refuses and names the missing words.

**Fix 3 (Page 3):** "After that fix, 'How does k-nearest neighbours classify a point?' is wrongly refused because 'classify' and 'point' are not word-for-word in the passages." → Retriever now treats word variants as the same (classify/class, point/sample, scaled/scale, √dk/√dₖ).

**Fix 4 (Page 3):** "On a phone the evidence list shows all 23 passages and is very long. Show the top 6 with a 'Show all' button; citations should still jump to passages that are hidden."

**Fix 5 (Page 2):** "The 'Try this' overfitting task doesn't show a clear drop at the default noise. Tell the user to raise the noise first."

## Adding tool 4: DSA Study Hub

### Prompts

> i wanna add DSA study hub also so now tell what else should add to the notebooklm and the this one

> see i dont want any cp dsa i just need good dsa thing like for clg students and for job level dsa

- I made a second notebook, **[DSA for College & Placements](https://notebook.google.com/notebook/98f130de-72b3-40ac-baf9-5136ce1efd53)**, with 20 links: Open Data Structures, MIT 6.006 lecture notes, Jeff Erickson's DP and greedy chapters, 10 Tech Interview Handbook cheat sheets, and the Interview Cake Big-O sheet. I also added my own DSA notes.
- I generated a study guide, mind map, flashcards and quiz in it, and checked it cites sources and refuses off-topic questions.

### Page prompt (4-part format)

- **WHO:** college students revising DSA for exams, and job seekers preparing for coding interviews.
- **WHAT:** a DSA study hub grounded in my DSA notebook. Every topic, card and quiz explanation is tagged with the source it comes from.
- **DO:**
  - Learn tab: a 26-topic checklist with progress, and a Big-O cheat sheet for data structures and sorting.
  - Visualiser: 7 algorithms (bubble, selection, insertion, merge, quick sort; binary and linear search) with play/pause, step forward/back, size and speed sliders, sorted/reversed input, and comparison/swap counters.
  - Practice: a "Which pattern?" quiz shuffled from 16 questions, and a tracker for 30 classic interview problems (Todo → Solved → Revise) with topic and status filters.
  - Revise: 18 flip-cards with search and shuffle.
  - Dark mode, saved progress, and a reset that asks for a second tap.
- **RULES:** one HTML file, no internet needed, works on a phone, matches the style of tools 1–3, facts must match the sources.

### Testing and fixes

- Each sorting algorithm ran on 300 random, sorted and reversed arrays and always ended correctly sorted. Binary search found the right item (or correctly reported "not found") every time, never using more than log₂ n + 1 comparisons. Quick sort on reversed input shows its O(n²) worst case.
- **Fix:** the page loaded but nothing worked, because the example tag in the checklist intro had no source number, so one line crashed and stopped the rest of the script. Added the number and made the source lookup safe.
- All four tabs checked at phone width (390 px): no sideways scrolling and no errors.

