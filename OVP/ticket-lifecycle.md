# Ticket lifecycle during the transition phase

For the OVP services, the ticket and deployment lifecycle are tightly coupled and intertwined, hence the need for this document. The purpose of this document is to document the entire lifecycle of what the different stages are when doing a ticket; starting working on it up to deploying to production.

## I have been assignment a ticket as a developer, how does the lifecycle work?

For a developer, the lifecycle for a ticket begins when it has been analyzed and is ready for implementation and assigned to you. For instructions on how to deploy the code, follow the instructions on [this page](https://github.com/Opetushallitus/dev-toolkit-private/blob/main/OVP/deployment.md).

Following is a step-by-step outline of the entire lifecycle process

1. Begin your work on the ticket. Open up a new branch in the repository you will make code changes to. **Follow the guidelines** outline in our [Git/GitHub guidelines document](../docs/git-github.md).
   1. Most of the time, you should be able to do the work and fully locally, without the need to test it by deploying it anywhere. However, if you need to test the changes in one of the test environments, you can deploy your branch by following the instruction on the page linked above.
   2. If you are stuck or unsure about something, a good starting point is to ask for further instructions or help via Slack. It is much better to ask for help than being stuck by yourself!
2. When you are ready and satisfied with your work, the changes must be reviewed by another developer. To facilitate this, you need to open a pull request on Github. Use the master/main branch as the target branch. Once again, **follow the guidelines** outline in our [Git/GitHub guidelines document](../docs/git-github.md). When you are done, move the ticket to the next stage on the Kanban board (_Katselmoinnissa_), remove yourself as the assignment person, and flag the ticket. In the next daily meeting, the ticket will be assigned to another developer for review.
   1. You can flag the ticket by right-clicking the ticket and selecting _Add flag_.
3. Once the review is completed and your pull request is approved, you can deploy your changes for acceptance testing. **DO NOT MERGE YOUR CHANGES AT THIS POINT YET!** Follow the instructions on the page linked above on how to deploy your changes. When you are done, move the ticket to the next stage on Kanban board (_Testauksessa_), remove yourself as the assignment person, and flag the ticket. In the next daily meeting, the ticket will be assigned for testing to the relevant person.
   1. If you for whatever reason cannot deploy your changes to any of the test environments yet, move the ticket to the _Jonottaa testauksessa_ stage on the Kanban board
4. Once your changes have been tested and approved, the changes can be deployed to production. Move the ticket to the _Odottaa tuotantoasennusta_ stage on the Kanban board if you do not intend to deploy your changes instantly. Being by **completing the pull request and merging the changes to the master branch.** Afterwards, follow the instructions on the page linked above to deploy your changes to production.
   1. NOTE! After you have deployed your changes to production, **you also need to also deploy the master branch to the environment you deployed your changes during the testing phase!** This frees up the environment for others to deploy to and keeps the environments up to date and clean.
