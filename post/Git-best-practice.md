
## <a name='TOC'>Contents</a>
1. [Start working with Git](#git)
2. [Commit best practice](#Commit)
3. [Merge requests](#Merge)
4. [Branches in the projects](#Branch)

## <a name='git'>Start working with Git</a>
To start working with Git, first of all, you must [download it](https://git-scm.com/downloads) and [install](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
After that, generate SSH key (here is an instruction how to do that https://docs.gitlab.com/ce/ssh/README.html).
Then, you must add your username and email to git global config https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup

## <a name='Commit'>Basic Rules of Committing</a>
### Commit often
Committing often keeps your commits small and, again, helps you commit only related changes. Moreover, it allows you to share your code more frequently with others. That way it‘s easier for everyone to integrate changes regularly and avoid having merge conflicts. Having few large commits and sharing them rarely, in contrast, makes it hard to solve conflicts.
### Don't commit half-done work
You must commit the code only after it is completed.This does not mean that you must complete a full feature before committing. On the contrary: divide the implementation of feature into logical fragments and remember what to do before and often. But don‘t commit just to have something in the repository before leaving the office at the end of the day.

### Test your code before you commit
Test it thoroughly to make sure it really is completed and has no side effects (as far as one can tell).

### Write Good Commit Messages
Begin your message with a short summary of your changes (up to 50 characters as a guideline). Separate it from the following body by including a blank line. The body of your message should provide detailed answers to the following questions: – What was the motivation for the change? – How does it differ from the previous implementation? 

__Example 1__ (no description, only summary)

```
  commit 3114a97ba188895daff4a3d337b2c73855d4632d
  Author: [removed]
  Date:   Mon Jun 11 17:16:10 2012 +0100

    Update default policies for KVM guest PIT & RTC timers
```


__Example 2__ (description as bullet points)
```
  commit ae878fc8b9761d099a4145617e4a48cbeb390623
  Author: [removed]
  Date:   Fri Jun 1 01:44:02 2012 +0000

    Refactor libvirt create calls

     - Minimize duplicated code for create

     - Make wait_for_destroy happen on shutdown instead of undefine

     - Allow for destruction of an instance while leaving the domain
```

__Example 3__ (description as plain text)

```
  commit 31336b35b4604f70150d0073d77dbf63b9bf7598
  Author: [removed]
  Date:   Wed Jun 6 22:45:25 2012 -0400

    Add CPU arch filter scheduler support

    In a mixed environment of running different CPU architecutres,
    one would not want to run an ARM instance on a X86_64 host and
    vice versa.

    This scheduler filter option will prevent instances running
    on a host that it is not intended for.

    The libvirt driver queries the guest capabilities of the
    host and stores the guest arches in the permitted_instances_types
    list in the cpu_info dict of the host.

    The Xen equivalent will be done later in another commit.

    The arch filter will compare the instance arch against
    the permitted_instances_types of a host
    and filter out invalid hosts.

    Also adds ARM as a valid arch to the filter.

    The ArchFilter is not turned on by default.
```
Sources:
1. https://github.com/trein/dev-best-practices/wiki/Git-Commit-Best-Practices
2. https://about.gitlab.com/2014/09/29/gitlab-flow/
## <a name='Merge'>Merge request</a>
Merge requests are useful to integrate separate changes that you've made to a project, on different branches.
Instruction how to create a merge request 
https://docs.gitlab.com/ee/gitlab-basics/add-merge-request.html. 
We use Merge request for team members can review the code and help with the resolving conflicts. 
## <a name='Branch'>Branches in the projects</a>
We work with next branches:
- features branches
- develop
- master
### We have some rules in working with them:
1. Branch out from develop
2. Never push into develop or master branch. Make a Merge Request.
3. Update your local develop branch and do an interactive rebase before pushing your feature and making a Merge Request.
4. Delete local and remote feature branches after merging.
5. Before making a Merge Request, make sure your feature branch builds successfully and passes all tests (including code style checks).