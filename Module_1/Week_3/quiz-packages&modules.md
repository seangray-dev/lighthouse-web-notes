## Question 1:

What purpose does the `require()` method serve in JavaScript?

## Answer:

It imports functionality (or data) from another module

Correct, it allows us to import functions, variables, and objects that are exported by other moduless

## Question 2:

To which directory does NPM install dependencies?

## Answer:

`./node_modules`

Each dependency has its own subdirectory in the `node_modules` directory

## Question 3:

Which of the following best explains the difference between packages, modules, and libraries?

## Answer:

- Library: an independent collection of code that can be used by programs (not JS specific)
- Module: JS code in a separate file, that can be required by other JS programs
- Package: a collection of JS modules, with a package.json, usually published on NPM

## Question 4:

Should the node_modules directory be committed to your project's git repo?

## Answer:

No. `package.json` should be commited because it contains the information necessary to recreate `node_modules`. Including `node_modules` would be redundant and would cause giatn git commits everytime a library is updated.

## Question 5:

Should the `package.json` file be committed to a project's git repo?

## Answer:

Yes. `package.json` should be commited, because it defines all the dependencies of your project, which are necessary to recreate the project from a fresh clone of the repository.
