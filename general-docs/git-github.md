# Git/Github

## Common guidelines

When using Git, here are some common guidelines. For all of these, the fictive example will use a ticket identifier of `TICKET-123` where the work is _"a new button under form X"_

- **When opening up a new branch** and working on a ticket, use the ticket identifier as a prefix to the branch. For example, name your branch `TICKET-123_<some text>`. You can replace `<some text>` with a few word description of the ticket, or omit it completely.
- **When committing code**, write your commit message in the format `<descriptive tag>: <message>`. A non-exhaustive list of descriptive tags include `feat` (i.e. feature), `fix`, `test`, `WIP` (i.e. work-in-progress), `docs` (i.e. documentation), `debug`, and `style`. Defaulting to use `feat` is fine. The purpose is to make it easier to recognize what the changes in the commit is about, especially during PR reviews
- **When opening up a new pull request (PR)**
  - Set the PR title to be of the form `<ticket identifier>:<descriptive title text>`. For example, `TICKET-123: Add a new button under form X`
  - For the description: if you would be the reviewer, what information/details would be good for you to have when reviewing the code? No need to write an essay, keep it concise! In addition to a concise description of the changes, here is a checklist of things that can be relevant to add:
    - How have the changes been tested/verified? Locally or in a different environment?
    - Have you added/modified tests
    - Have you updated the documentation if needed?

## GitHub settings
