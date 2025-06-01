# counting-task-llm-benchmark

### Task description
Given a prompt of the form: *"Count the number of words in the following list that match the given type, and put the numerical answer in parentheses.
    Type: animal, List: [cat tiger book dog keyboard clock bottle chair]
    Answer: "*
how well do different LLMs perform, i.e., return the correct answer (3)?

Is there a layer that keeps a running count of the category of interest while parsing the list? Can we identify this layer using activation patching, i.e., causal mediation analysis?
##
### Dataset generation
- **Notebook**: dataset-generator.ipynb
- **Dataset**: word_counting_dataset.jsonl

Contains 5000 samples (lists) of length 5-15 with somewhere between 0-10 elements that belong to one of the categories *fruits, cities, animals, sports, professions* with (any) remainder spaces being taken up by miscellaneous words that belong to none of those categories.

### Benchmarking
- **Notebook**: benchmarking-llms-word-counting.ipynb
- **Results**: evaluation_results_20250531_223253.csv

Models benchmarked include *Mistral-7B-Instruct-v0.3, Llama-3.2-3B-Instruct, gpt2-large, Falcon3-7B-Instruct.*

### Activation patching
- **Notebook**: patching-analyses-running-count.ipynb
- **Controls dataset and responses**: controlled_counting_dataset.jsonl, clean_responses_controlled_dataset.csv

Using two types of positive and negative controls each, perform layer-wise activation patching at evenly spaced layers of the LLM to see if any of then show significant changes in task behaviour.

### Additional patching anlayses experiments
- **Notebook**: patching-analyses-running-count-intermediate-layers.ipynb
- **Controls dataset and responses**: intermediate_controlled_counting_dataset.jsonl, intermediate_clean_responses_controlled_dataset.csv

Same analyses as original, but over all intermediate layers of Falcon3-7B-Instruct in the range 11-19. 

##
### <a href="https://docs.google.com/document/d/1G1wDiawjMcs6DaLrHhZPidSTU1uPQRVvEoVfZheiOlg/edit?usp=sharing" target="_blank">Summary doc</a>
