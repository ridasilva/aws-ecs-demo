# aws-ecs-demo
This repository is protected under the `BSD 3-Clause License` which can be found in `LICENSE.md`.

Demo repository for pushing boiler-plate Flask app to AWS ECS.

`docker-compose.yml` is only for testing the application on your local machine and not in used in the AWS deployment.

Youtube playlist link: https://www.youtube.com/playlist?list=PL0dOL8Z7pG3IWsvseNd-JoFTHL16P_iTC

---

### AWS Code Snippets:
AWS Secrets Manager - restrict access by IAM role

```
{
  "Version" : "2012-10-17",
  "Statement" : [ {
    "Effect" : "Deny",
    "Principal" : {
      "AWS" : "*"
    },
    "Action" : "secretsmanager:GetSecretValue",
    "Resource" : "*",
    "Condition" : {
      "StringNotLike" : {
        "aws:userid" : [ "AIDATC....", "AIDAT...." ]
      }
    }
  } ]
}
```
Additional notes:
* Access aws:userid with `aws-cli` and `aws iam get-user --user-name {aws-iam-user-name}`
