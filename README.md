# FactParser
An overly-ambitious goal of creating a project to take a block of text (story, paragraph, etc.) and extract the facts from it for use in downstream systems (chatbots?).

The (perhaps mistaken) assumption is that language is used to communicate facts and ask questions. The basic questions that can be answered with language are:
Who? 
What? 
When? 
Where? 
Why? 
How? 
How much?

In most languages, verbs boil down to a few basic verbs that cover most ideas (https://www.englishclub.com/vocabulary/common-verbs-25.htm).

An assumed rough approach to extract facts from a paragraph would be to do the following:
1. Load a text
2. Break it into sentences (maybe this would be optional?)
3. Identify subjects, verbs, objects (into an SVO model)... surprisingly difficult to do.
4. Identify which subjects are the same amongst different sentences. Challenging due to pronouns.
5. Once subjects are identified, for each sentence where the subject is referenced, process verbs and objects to extract. 
6. Insert into data structure, with subject being key, and subdetails being children/subkeys
7. Query info

I first started out by learning a small amount how to use NLTK, which is great but has perhaps too many levers to be quickly useful. It's like a box of nails, some wood, and a hammer... maybe some steel poles, screws, and a drill would be better for this task. So I began looking for what others had already done.

I found this question, which provided several approaches for how to tease out the S-V-O components, but fails due to pronouns and indirect references within a paragraph. It did, however, lead me to examine the spaCy library.
https://stackoverflow.com/questions/39763091/how-to-extract-subjects-in-a-sentence-and-their-respective-dependent-phrases

Noting the above, I then started to explore the spaCy library, how it's used, and found that others have already created a coreference engine, https://github.com/huggingface/neuralcoref. This allows us to know, with a reasonable degree of accurracy, which subjects and objects are recurring in various sentences, so that we can map each topic to its supporting sentences (remember, while perfect mapping would be nice, we have to start *somewhere* first).

