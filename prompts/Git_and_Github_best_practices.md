Let's look at some best practices for using Git and GitHub we follow at BigBinary. This will make our workflow consistent and efficient.

Linking Tasks to GitHub Issues
Every task you work on must have a corresponding GitHub issue. Create issues in the future tense. For example, if you're working on a test case called Login to the application, raise a GitHub issue titled "Add Playwright tests to verify logging in to the application".

Branch Naming Convention
Branches should be named in the future tense and follow this format:<issue_number>-a-short-hyphenized-description-of-the-issue.

For example: 2-add-tests-to-verify-login

Atomic Commits
Make small, logical commits. Do not commit all changes for an issue in a single commit. Instead, break down the feature into smaller parts and commit after each part is completed.

Meaningful Commit Messages
Add logical commit messages. You should NOT add commit messages like Completed first part or Fixed review suggestion.

Instead, you should add meaningful messages such as Added beforeEach block for login tests or Fixed redundant awaits in the code.

PR Description Format
When raising a pull request (PR), the first line of the description should be:

- Closes #<issue-number>
For example, if the issue number is 1, the PR description should start with:

- Closes #1
Past Tense for Commit Messages
Commit messages should be in the past tense because they describe work already completed. For example:

Added tests to verify logging into the application
Fixed tests failing due to page closing unexpectedly.
Past Tense for PR Titles
PR titles should also be in the past tense, summarizing the work done in the PR. While commit messages focus on individual changes, the PR title summarizes the entire feature. Example PR titles:

Added tests for login
Added tests to verify tasks assigned to the same user
Frequent Pushes and Draft PRs
Push your commits to GitHub frequently. Once the first commit is made, create a draft PR and continue pushing commits to it. This ensures your code is safe and also lets the reviewers know about your progress in an issue.

Note: If you cannot create a draft PR in your personal GitHub repository, it's okay to raise a regular PR.

Assign PRs for Review Only When Ready
Do not assign a PR to a reviewer until it is fully ready for review. Assigning too early can overwhelm the reviewer with notifications. Assign it only when the work is complete and fully functional.

Assign the PR to the Reviewer
When the PR is ready for review, make sure to assign it to the reviewer. Simply adding them as a reviewer does not subscribe them to updates. Assigning them ensures they receive notifications about new events on the PR.

github-assigned.png
Prioritize Review Comments
Address review comments before starting new features. This ensures your PR gets approved and merged faster.

Merge Only After Approval
A PR should only be merged once it has been fully approved by the reviewer.

Responding to Review Comments
When you get review comments, the PR will be assigned back to you. Once the requested changes are completed and pushed assign the PR back to the reviewer and post a comment saying you have fixed the review comments.
