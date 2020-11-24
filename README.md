# Quda: Natural Language Queries for Visual Data Analytics

<!-- Detailed introduction of Quda can be found in: [arxiv](www) -->

## About

In the context of visualization-oriented natural language interfaces, Quda contains 14,035 diverse user queries annotated with 10 low-level analytic tasks that assist in the deployment of state-of-the-art machine/deep learning techniques for parsing complex human language.

## Characteristics

### Abstraction: Low.

The abstraction level describes how concrete a query is.

### Composition: Concrete.

The composition level describes to what extent a query encompasses sub-queries.

### Perspective: Objectives.

Instead of enumerating actions, we aim to collect queries that are objectives raised by data analysts.

### Type of Data: Table.

Data and dataset can be categorized into five types, i.e., table, networks & trees, fields, geometry, and clusters & sets & lists.

### Type of Tasks: 10 Low-level Tasks.

Include Retrieve Value, Correlate, Compute Derived Value, Find Anomalies, etc.

### Context Dependency: Independent.

Focus on queries that have complete references to tasks or values associated with a task.

## Dataset Preview ([Download](https://github.com/freenli/quda_corpus))

| Retrieve Value  | Filter | Compute Derived Value | Find Extremum | Sort | Determine Range | Characterize Distribution | Find Anomalies | Cluster | Correlate |
| --------------- | ------ | --------------------- | ------------- | ---- | --------------- | ------------------------- | -------------- | ------- | --------- |
| 1               | 2      | 3                     | 4             | 5    | 6               | 7                         | 8              | 9       | 10        |    


| id  | task_id | exp_sen_id | is_exp_sen | table_id | expert_id | sentence                                                                                      |
| --- | ------- | ---------- | ---------- | -------- | --------- | --------------------------------------------------------------------------------------------- |
| 1   | 1       | 1          | 0          | 1        | 1         | show me arkansas' population on july 1 , 2002 .                                               |
| 2   | 1       | 715        | 1          | 35       | 16        | how many residents in orange county are asians ?                                              |
| 3   | 2       | 90         | 0          | 11       | 3         | can you tell me the team that won the game ?                                                  |
| 4   | 2       | 91         | 1          | 7        | 3         | which country has more females than males ?                                                   |
| 5   | 3,2       | 105        | 0          | 3        | 4         | in western europe , what is the average gdp ?                                                 |
| 6   | 3,2       | 171        | 1          | 13       | 5         | on average , how long are the books published by dark horse comics ?                          |
| 7   | 4       | 246        | 0          | 15       | 6         | i would like to have the highest rating number .                                              |
| 8   | 4       | 262        | 1          | 1        | 1         | what is the longest study time that students have ?                                           |
| 9   | 5,2       | 358        | 1          | 15       | 7         | list all the expensive apps , from the most recent to the oldest .                            |
| 10  | 5       | 378        | 0          | 22       | 8         | list all the movies according to their release year .                                         |
| 11  | 6       | 433        | 1          | 24       | 9         | what is the range of the number of undergraduate students ?                                   |
| 12  | 6,2       | 491        | 0          | 26       | 10        | in the south american countries , how large is the range of registered soccer players ?       |
| 13  | 7,2       | 770        | 0          | 36       | 17        | determine the value distribution of deaf -blind patients .                                    |
| 14  | 7,2       | 810        | 1          | 32       | 18        | show me the distribution of the population ratio binned with a bin size of 0.5 .              |
| 15  | 8       | 236        | 1          | 15       | 6         | is there any app that is significantly different from the others ?                            |
| 16  | 8,1       | 441        | 0          | 24       | 9         | identify the anomalous values of both postgraduate and undergraduate income .                 |
| 17  | 9       | 916        | 0          | 32       | 20        | group the length of trip by initial sites .                                                   |
| 18  | 9,4       | 532        | 1          | 27       | 11        | find the cluster with the highest number of births among the neighborhoods across the years . |
| 19  | 10      | 80         | 1          | 3        | 2         | can we infer that higher freedom leads to higher happiness ?                                  |
| 20  | 10      | 613        | 0          | 30       | 13        | are the ages of the actors and their winning results correlated ?                             |

- task_id: task id of the sentence (1-10)
- exp_sen_id: expert sentence id of the sentence (1-920)
- is_exp_sen: whether the sentence is the expert sentence (0: no, 1: yes)
- table_id: table id of the sentence (1-36)
- expert_id: expert id of the sentence (1-20)

## License

It is released for non-commercial use under the CC BY-NC-SA 3.0 license.
