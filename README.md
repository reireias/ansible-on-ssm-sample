# ansible-on-ssm-sample
Sample code for running Ansible on AWS System Manager.

## Create EC2 Instance
- tag: Key = Env, Value = test
- IAM Role: Attach Role which has AmazonSSMManagedInstanceCore Policy

## Run Ansible on SSM
```console
$ aws ssm send-command \
    --document-name "AWS-ApplyAnsiblePlaybooks" \
    --parameters '{"SourceType":["GitHub"], "SourceInfo":["{\"owner\": \"reireias\", \"repository\": \"ansible-on-ssm-sample\", \"getOptions\": \"branch:master\"}"], "InstallDependencies":["True"], "PlaybookFile":["playbook.yml"]}' \
    --targets "Key=tag:Env,Values=test" \
    --comment "echo HelloWorld"
 ```
