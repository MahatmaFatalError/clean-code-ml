# clean-code-ml lesson plan

### outline
- Why do we need clean code? (A: change and complexity)
- What does bad code / clean code look like?
- How do we clean up code in an existing data science / ml codebase? (exercise in refactoring titanic notebook)
    - go through refactoring process below
- How do we write clean code in a new project?

### Refactoring process (for an existing notebook)

My process for refactoring the titanic notebook
- Ensure that notebooks when run from start to end
- Read notebook and list code smells (see next section)
- Make a copy of the original notebook (for comparing the end result later)
- Start refactoring 
    - Identify a block of code that can be extracted into a pure function, and extract it into a pure function
    - Write a unit test for it
    - Move function into a Python module
    - Import function back into the notebook
    - Restart and run entire notebook (Unfortunately, until we have sufficient unit tests, we will still need manual “integration” tests for the time being.)
    - Rinse and repeat

### Code smells
- too many comments
- bad variable names
    - train_df and test_df could be better named (without type information)
    - combine
- too many print statements
    - df.info(), df.head(), df.describe(), etc. - is there any other way that we can get feedback on the data?
- no tests for data transformations (e.g. cell 17 onwards)
- cell 18, 19 (mutation to `dataset` outside of a function)
- duplication in model training code. Can extract to a function.
- duplication in EDA code. Can extract to a function.
- duplication in how test_df and train_df are joined. Why not just join it once, and use the combined df for all data transformations?


### How do we write clean code in a new project?
- It's ok to use notebooks if you need the feedback that it gives. But try to get rid of it (or keep it just for reference and stop adding new code to it) as soon as it has served its purpose of giving us feedback
- TDD
- Demo: tackle a new ML problem using TDD and clean code practices