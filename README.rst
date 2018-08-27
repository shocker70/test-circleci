
Continious Integration with CircleCI and Bitbucket

Requieres two branches in bitbucket, [ Master ] and [ test ], being Test a branch of Master.

When a [push] to Test branch happens, a automated test runs in CircleCI.

If CicleCI test runs correctly, 1EC istance is deployed in AWS.
