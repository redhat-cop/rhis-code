## Slack Integration
In this project, Slack is used as the centralized notification service.
We established an efficient communication channel where team members are
not allowed to send any messages, but only the integrated applications
can send notifications. This setup integrates seamlessly with our
development workflow, allowing us to stay informed about important
events in real-time.

!!! info

    We use following channel for notifications on Slack. [cop-rhis-notifications](https://redhat.enterprise.slack.com/archives/C06VCEWRQE4)

## GitHub Integration

We utilize GitHub and Slack integration to monitor new pull requests and
automated pipeline runs, ensuring that every team member is promptly
notified of any code contributions and/or workflow results.More
comprehensive customizations can be found in [this
repo](https://github.com/integrations/slack). To be able to use this
integration, GitHub app should be installed on Slack from
[here](https://redhat-external.slack.com/apps/A01BP7R4KNY-github?tab=more_info).

    # invite GitHub application and authenticate
    /invite @github

    # receive notifications only on pull request creation and workflow run
    /github subscribe redhat-cop/rhis-code workflows:{event:“pull_request”,“push” branch:“main”,“devel”}
    /github unsubscribe redhat-cop/rhis-code issues commits releases deployments

    /github subscribe redhat-cop/rhis-inventory workflows:{event:“pull_request”,“push” branch:“main”,“devel”}
    /github unsubscribe redhat-cop/rhis-inventory issues commits releases deployments
