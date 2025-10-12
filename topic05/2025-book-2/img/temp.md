
### Gitlab access to EC2.

We want to allow a Gitlab CI pipeline to interact with our EC2 instance over an SSH connection. To enable this interaction, we must:

+ Create a user using the AWS IAM service (Identity and Access Management service).
+ Generate public and secret access keys for the user.
+ Configure a Gitlab pipeline with those access key credentials. Any permissions granted to the user account are transferred to the pipeline automatically. 

Follow these steps to create the user via the AWS Management Console:

1. Type IAM in the search box of the page header, and select IAM from the matching list.
1. Click Users in the left panel.
1. Click the Create User button on the top right.
1. Enter cicduser for username.
1. Click Next.
1. For Set Permissions, choose Attach policies directly.
1. In the Permissions policies block, type EC2Contain into the search box and tick AmazonEC2ContainerRegistryFullAccess from the matching list.
1. Click Next
1. Review your options and click Create User.

A list of users is displayed, including the one you just created. Continue with the following steps:

1. Click the cicduser user to display the full details.
1. Click the Security Credentials tab.
1. Scroll down to the Access keys block and click the Create access key button.
1. For use cases, choose Command Line Interface (CLI).
1. Tick the Confirmation box at the bottom and click Next.
1. Click Create access key.
1. Click the Download csv file button (Very important) and click Done.

A file named `cicduser_accessKeys.csv` was downloaded to your laptop - we will use it in the next section to configure a Gitlab CI pipeline.
