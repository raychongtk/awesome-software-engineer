# Code Author Journey
Code review is common in software development, especially working with a team. People want to ensure code quality and reasonable design during code review and align engineering practices with team standards.

As a code author, you may receive a lot of comments from your teammates. Your teammate may suggest a better design for you, a better naming to describe a function, an improvement in code structure, and so on. Positive feedback can make you grow so don’t feel that people are blaming you.

Few things that I think it is important for a code author when creating Pull Request or your code is being reviewed by others:

## Be modest and open-minded

As a software engineer or code author, being modest is really important when working with a team. I know you are good but you shouldn't think you are the best one and reject all the ideas from others. Good ideas come from discussion and communication. If your reviewers give you some feedback and it can help you improve your code readability, consistency, or correctness, why not just accept it? Running a code review is like knowledge sharing to help the team to build good engineering culture and share engineering thoughts with teammates. These opportunities can help you and your team grow together and build a solid codebase. So, be modest and open-minded and try to accept good feedback from others.

## Write a descriptive title to your pull request  

When creating a pull request, you are responsible to write a descriptive title to let your reviewers know the background of your changes like attaching your Jira ticket number, type of change, and a short description for the change. If the title is not enough to describe your change, you should write something in the description to provide more background information to your reviewers. It can facilitate communication between you and your reviewers and make the pull request get approved faster because your reviewers do not need to ask you what you are changing and why you need to make the change. Your time shouldn’t be wasted in communicating the change background. So, make your pull request descriptive and help reviewers understand your changes are very important.

## Write small code changes

I know sometimes developers want to test the whole feature in the local environment before committing to Git. It is good that have tested on the local environment but remember if you push a large code change, people might feel it is hard to review. It takes a lot of time to understand a large code change saying 300+ lines. People usually do not want to review that large code change and they will simply leave LGTM to your pull request because it is hard to understand and takes a lot of time. Your reviewers are not only serving your pull request, they may have a lot of work pending to do. If you keep your code change small, people may find many issues for you and those comments can help you grow in your software engineering career. But, if you don’t, probably people will not review your code deeply. You may lose some learning chances from your peer sometimes.