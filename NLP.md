### 🧠 Natural Language Processing: Final Exam Master Summary

#### 1. The Core Definition and Computer Vision vs. NLP
**Natural Language Processing (NLP)** is an interdisciplinary field at the intersection of Computer Science, Artificial Intelligence, and Computational Linguistics. It bridges the gap between how humans communicate and how machines process information.
* **NLU (Natural Language Understanding):** The reading half. Extracting meaning (e.g., parsing, sentiment analysis, spam classification).
* **NLG (Natural Language Generation):** The writing half. Creating new text (e.g., machine translation, chatbots, summarization).

**CV vs. NLP (Key Differences):**
* **Data Representation:** Images are inherently numeric (pixels); text consists of discrete symbols that must be converted to numbers.
* **Size:** Images can be easily resized to a fixed grid; text sequences vary drastically in length.
* **Universality:** Images are universal; text is language-dependent.
* **Nature:** CV works with continuous, smooth data; NLP works with discrete, highly ambiguous data.

#### 2. NLP Applications and The Trap of Ambiguity
**Key Applications:**
* **Machine Translation (MT):** Evolved from rigid *Rule-based* (1950s) to *Statistical* (1990s) to modern *Neural MT* (Encoder-Decoder/Transformers).
* **Sentiment Analysis:** Extracting the subjective emotional tone (Positive/Negative/Neutral) from text.
* **Information Extraction (IE):** Pulling structured data from messy text, heavily relying on **NER (Named Entity Recognition)** to identify people, organizations, and locations.

**Why Language is Hard (Ambiguity):**
* **Word Sense Ambiguity:** When the same word has different meanings (e.g., "bat" the animal vs. "bat" in baseball).
* **PP Attachment Ambiguity:** Structural confusion where the grammar is a puzzle (e.g., "Cops kill man with knife" - who was holding the knife?).
* **Compositionality:** The meaning of a sentence depends heavily on how the words are combined, not just the individual definitions.

#### 3. Text Processing and Parsing
Before a computer understands meaning, it must map out the grammar.
* **POS Tagging (Part-of-Speech):** Assigning a grammatical category (Noun, Verb, Adjective) to every single word.
* **Constituency Parsing:** Determines "hierarchical phrase structure." It groups words into chunked units (e.g., building a Noun Phrase tree).
* **Dependency Parsing:** Determines direct grammatical relationships between words. It draws binary arrows from a "head" (boss) word to a "dependent" (employee) word. *Note: Highly effective for free word-order languages.*

#### 4. Text Representation: Turning Words into Numbers
To do math on text, we must weigh the importance of words.
* **Term Frequency (TF):** How often a word appears in a specific document.
    * *Formula:* $tf\text{-}weight = 1 + \log_{10}(tf_{t,d})$ (if $tf > 0$).
    * *Why Log?* Relevance does not scale linearly. Mentioning a word 100 times does not make the document 100 times more relevant than mentioning it once.
* **Inverse Document Frequency (IDF):** How rare the word is across the entire library.
    * *Formula:* $idf_t = \log_{10}(\frac{N}{df_t})$.
    * *Why?* Penalizes common words (like "the") and massively rewards rare, specific words.
* **TF-IDF:** The ultimate score. $Weight = TF \times IDF$.
* **The Vector Space Model:** Documents are represented as giant arrays of numbers (**sparse vectors**) in a geometric space ($\mathbb{R}^{|V|}$).
* **Cosine Similarity:** The computer measures the **angle** ($\theta$) between two document vectors. $\cos(\theta) = 1$ means they point the exact same way (highly similar).

#### 5. Word Embeddings (Word2Vec)
Upgrading from isolated word counts to actual "meaning."
* **Sparse vs. Dense:** TF-IDF creates *sparse* vectors (huge dimensions, mostly zeros). Embeddings create *dense* vectors (compact lists of numbers, e.g., 300 dimensions, where every number holds meaning).
* **The Distributional Hypothesis:** "You shall know a word by the company it keeps." Words with similar contexts end up clustered close together in the vector space.
* **Word2Vec Architectures:**
    * **CBOW (Continuous Bag of Words):** Predicts a missing target word based on its surrounding context words.
    * **Skip-gram:** Uses a single target word to predict the surrounding context words. (Often better for rare words).

#### 6. The Modern Era: Transformers & LLMs
The architecture that changed everything by reading whole sentences at once instead of word-by-word.
* **Self-Attention:** A mathematical mechanism that allows the model to look at one word and calculate how strongly it should pay "attention" to every other word in the sequence. 
* **Encoder vs. Decoder:** * **BERT:** Focuses on the *Encoder*. It reads bidirectionally to deeply understand context.
    * **GPT:** Focuses on the *Decoder*. It works autoregressively (left-to-right) to predict the next word.
* **Scale:** The massive power of modern Large Language Models (LLMs) is unlocked by simply scaling up three things: **Parameters**, **Data**, and **Compute**.

---

### ✅ Exam Procedure Checklist

* **If asked about CV vs NLP data representation:** Mention images are already continuous numeric data (pixels), while text is discrete symbolic data that requires conversion algorithms.
* **If asked why we use the logarithm in Term Frequency:** State clearly: "Because relevance is not linear. It dampens the effect of high-frequency words so a word appearing 100 times isn't given 100x the weight."
* **If asked to define the Distributional Hypothesis:** Quote or paraphrase: "Words that appear in similar contexts share similar meanings."
* **If asked about the difference in Parsing:** Remember: *Constituency* builds hierarchical chunked trees; *Dependency* draws direct grammatical arrows between words. 
* **If asked what happens to the IDF of the word "the":** Explain that because it appears in every document, the ratio $N/df$ becomes 1. The $\log_{10}(1) = 0$, completely zeroing out its weight.
