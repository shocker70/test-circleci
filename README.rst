
Continious Integration with CircleCI and Bitbucket

Basic HelloWorld Django application running. 

Requieres two branches in bitbucket, [ Master ] and [ test ], being Test a branch of Master.

When a [push] to Test branch happens, a automated test runs in CircleCI, if errors are found, they are reported back.

When a [push] to Master from test happens a automated test runs in CircleCI, if no error found, Anible PLAYBOOK RUNS.

      + 1EC istance is deployed in AWS, with Django HelloWorld.
     
     
[[ Project still on process ]]
