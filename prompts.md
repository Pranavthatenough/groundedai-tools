# Prompts and build log

How these six tools were built with an AI agent, without writing code by hand.

- **Agent:** Claude
- **Notebooks behind the tools:**
  - [GroundedAI](https://notebook.google.com/notebook/c8a75025-8605-4f81-aba1-88c6b47f8669) (ML): Dive into Deep Learning, Google ML Crash Course, *Attention Is All You Need*, scikit-learn docs, PyTorch tutorials and my own notes.
  - [DSA for College & Placements](https://notebook.google.com/notebook/98f130de-72b3-40ac-baf9-5136ce1efd53): Open Data Structures, MIT 6.006 lecture notes, Jeff Erickson's *Algorithms*, Tech Interview Handbook cheat sheets, the Interview Cake Big-O sheet and my own notes.

Every page prompt uses the same 4-part format: **who** it's for, **what** it is, what it should **do**, and the **rules**.

## Part 1: the ML tools

### Giving the agent context
I described my GroundedAI notebook: AI that answers only from verified reference sources and cites every claim, plus its list of ML references. I asked for interactive pages that turn the notebook into tools I can click. (The agent couldn't open the notebook link itself, because Google blocks automated access, so I described it.)

### Page 1: ML Revision Dashboard
- **WHO:** Me, revising the ML topics from my GroundedAI notebook before an exam.
- **WHAT:** A study hub for AI vs ML vs DL, supervised and unsupervised learning, classical ML, deep learning, Transformers and grounded AI. Every item tagged with the notebook source it comes from, e.g. [3] = *Attention Is All You Need*.
- **DO:** Topic checklist with a progress ring and per-group bars; exam countdown with a date picker and daily pace; flip-cards with topic filter, search, status filter, shuffle, flip-all and "knew it / review again" marks; a 10-question scored quiz with explanations, skip and a review screen; clickable source tags; dark mode; reset-all.
- **RULES:** One HTML file, no internet needed, works on a phone, facts must match the sources, progress saved in the browser, check every button works.

### Page 2: Classification Playground
- **WHO:** A student learning how classifiers work (scikit-learn / ML Crash Course chapters).
- **WHAT:** A 2D plot where a classifier draws its decision boundary live, plus train vs test accuracy, precision, recall and a confusion matrix, so overfitting is visible.
- **DO:** Dataset switch (blobs, moons, circles, XOR); noise, point-count and test-split sliders; new sample; model switch (k-NN / logistic regression); k slider; linear vs polynomial features; learning-rate slider; animated training with a loss curve; +1 step; reset weights; click to add points; undo; show/hide test points; confidence shading; an overfitting/underfitting message.
- **RULES:** One HTML file, plain JavaScript (no libraries), works with touch on a phone, realistic sample data, explain each model in plain words with its source.

### Page 3: Grounded Answer Lab
- **WHO:** Classmates and teachers who want to *see* why source-grounded AI is more trustworthy than a chatbot answering from memory.
- **WHAT:** A mini notebook of short passages from my 6 sources. You ask a question; it retrieves and ranks passages, answers only from them with clickable [1][2] citations, and says "Not in my sources" when the evidence is weak. Next to it, a simulated memory-only chatbot with planted mistakes to spot.
- **DO:** Question box and preset questions (including off-topic ones); Compare / Grounded / Memory switch; source on/off toggles; top-k slider; relevance-threshold slider; highlight matched words; "Spot the problems"; citations that jump to the evidence; a "claims with a citation" meter; reset.
- **RULES:** One HTML file, no internet, works on a phone. Passages are my own short summaries (no copied text). Memory answers clearly labelled as simulated.

### Fix rounds (found by testing every control at laptop and phone size)
1. **Playground:** the confidence shading showed a grid pattern → it is now drawn as a small image and scaled up smoothly.
2. **Answer Lab:** "best learning rate for ResNet-50 on ImageNet" was answered from a general learning-rate passage → added a gap check: if key words in the question appear nowhere in the notebook, it refuses and names them.
3. **Answer Lab:** after that, "How does k-nearest neighbours classify a point?" was wrongly refused → the retriever now treats word variants as the same (classify/class, point/sample, √dk/√dₖ).
4. **Answer Lab:** on a phone the evidence list was very long → shows the top 6 with a "Show all" button; citations still jump to hidden passages.
5. **Playground:** the "Try this" overfitting task didn't show a clear drop at the default noise → the task now says to raise the noise first.

## Part 2: the DSA tools

### Building the DSA notebook
> i dont want any cp dsa i just need good dsa thing like for clg students and for job level dsa

I made a second notebook, **DSA for College & Placements**, with 20 links (Open Data Structures, MIT 6.006 lecture notes, Jeff Erickson's DP and greedy chapters, 10 Tech Interview Handbook cheat sheets, the Interview Cake Big-O sheet) and my own DSA notes. I generated a study guide, mind map, flashcards and quiz in it, and checked that it cites sources and refuses off-topic questions.

### Page 4: DSA Study Hub
- **WHO:** College students revising DSA for exams, and job seekers preparing for coding interviews.
- **WHAT:** A DSA study hub grounded in my DSA notebook. Every topic, card and quiz explanation is tagged with its source.
- **DO:** Learn tab with a 26-topic checklist and a Big-O cheat sheet; a visualiser for 7 algorithms (bubble, selection, insertion, merge and quick sort; binary and linear search) with play/pause, step forward/back, size and speed sliders, sorted/reversed input and comparison/swap counters; a "Which pattern?" quiz and a tracker for 30 classic interview problems; 18 flip-cards; dark mode; saved progress.
- **RULES:** One HTML file, no internet needed, works on a phone, matches the style of tools 1–3, facts must match the sources.

### Page 5: Data Structure Playground
> look at the other 2 pages of groundedai ml one just like that i want pages for dsa also

- **WHO:** A student who knows the Big-O table by heart but has never *watched* a structure slow down.
- **WHAT:** The DSA version of the Classification Playground: a live drawing of a data structure where every operation is animated step by step and counted.
- **DO:** Six structures (stack, queue, BST, min-heap, hash table, graph). Push/pop, enqueue/dequeue, insert/search/delete, extract-min, BST traversals (in/pre/post/level order), BFS and DFS from any start node (tap a node). "Insert 1–10 in order" vs "Insert 10 random" for the BST, a bucket slider and a worst-case hash for the hash table, a random-graph button, an animation-speed slider. A "What did that cost?" panel with step counts and the Big-O cost, an alert like the overfitting message (unbalanced tree, high load factor, all keys colliding), an explanation with source tags, and "Try this" tasks.
- **RULES:** One HTML file, plain JavaScript, works on a phone, matches tools 1–3, explanations cite the DSA notebook.

### Page 6: DSA Answer Lab
- **WHO:** The same audience as the ML Answer Lab, now for DSA.
- **WHAT:** The Grounded Answer Lab rebuilt on 24 passages summarising my DSA notebook's sources.
- **DO:** Everything the ML lab does. Preset questions on quick sort, binary search, stack vs queue, hash tables, dynamic programming and sorted BST inserts, each with a memory chatbot making a classic mistake; two off-topic presets (a Codeforces rating, the World Cup) that must be refused.
- **RULES:** Same as page 3. Passages are my own summaries; memory answers are labelled simulated.

### Testing and fixes
- **Study Hub:** every sorting algorithm ran on 300 random, sorted and reversed arrays and always ended sorted; binary search never used more than log₂ n + 1 comparisons. **Fix:** the page loaded but nothing worked, because one source tag had no number → added it and made the lookup safe.
- **Playground:** clicked every operation on all six structures. Checked the BST stays correct over 200 random insert/delete runs (inorder always sorted), the heap order always holds and extract-min returns keys in sorted order, and BFS reaches every node with correct distances on 40 random graphs. **Fixes:** on a phone the drawing was shrunk so much the numbers were unreadable → circles, boxes and text are bigger on small screens; the heap's "array" label was cut off → moved above the array; "1 swaps" → "1 swap".
- **Answer Lab:** every on-topic preset gets a cited answer and both off-topic ones are refused, as are other off-topic questions (baking a cake, React libraries). **Fix:** "When should I use a heap?" ranked a sorting passage first because it mentioned "heap sort" → reworded that passage.
- All pages checked at laptop and phone width (390 px): no sideways scrolling and no errors.
