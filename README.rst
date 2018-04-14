
FIRST PART OF THE TEST:
=======================
For the first part of the test I had to studdy the different tools that i could use for CI, not being able to use Attlasian tools.

When I started the first tools i thought that could match the team workload where:
    + Travis CI
    + CircleCI 
    + Jenkins

Lets have a closer look at each one:
  
    TravisCI:

PROS:
This tool is based on cloud solution, and runs over docker to execute the tests. 
One of the strong sides of TravisCI i consider is that it supports build matrix, allowing you to run test with different versions of the same lenguaje at the same time.

CONS:
Well travisCi also has some bad things, it has no free enterprise plan, and prices are quite expensive, and for me one of the worst things it has is that there are not too many 3rd partys that support it.

    CircleCI:
CircleCI and TravisCI are quite similar.

PROS:
CircleCI is also cloud Base but it offers the chance to run it on cloud or on your own datacenter. ( But need to ask for the enterprise free trial and takes one day minimun, this slowed me down a little bit )
CircleCI also runs over docker to execute tests.
It also alows you to connect via ssh to the dockers running for a more in depth search of the problem.

CONS:
It dosent support a great amount of programing lenguajes.


----- Jenkins:
Jenkins whas also one of the solutions i could aproach, but i wanted to test something different, and Jenkins requires a big configuration that may take longer to make it work properly.


SOLUTION:

So alfter this little ressume, i thought that the best tool whas CircleCI, the user interface looked very friendly and its high customizable. One of the biggest reason i thought that CircleCI 
will be better than TravisCI is that its supported by much more 3rd partys and this will alow the project to grow with many more chances.

How it will work:
1. The developers will make changes on the local version, once they made them commit their changes.

2. Once the Account manager merges the changes into the STAGING Branch named ( test ) in my example, the repo will send a hook to CircleCI.

3. Once CircleCI recieves the hook it will start running the tests, syntax check and others

4. Now all the pre-configured testing can run in cirlce ci automatically.

5. If a test fails, circleCI shows in red, and can alert the team.

6. If all is OK, then when the STAGING branch is merged to the MASTER(prod) circleCI can make the deploy into the dessired servers.


*For the 6th step: On this example i dont deploy the code into any machine but i run a little ansible play book just to show that tools like ansible can be used to automate deploys via circleci.

Important: One of the ideas also is that the code that is just commited by the developer can trigger a CircleCI workflow and be tested immediatly, making errors visible faster and eassiers.



SECOND PART OF THE TEST:
========================
"" For the second part of the test i had some confusion, at first i thought that the idea was to make the deploy of the code once it passed the test via CircleCi.
The idea i had was to run a ansibleplaybook that did the deploy if all the tests passed.""

For the second part of the test i had to make a deploy of circleCI on the cloud.
I have a freetier account on AWS so i used it to make the deploy on a ec2  minimal instance. And decided to use Ansible as the deployment tool.

I had a big advantaje on this part because CircleCI has an AMI on AWS, so i made with Ansible a playbook to deploy the EC2 instance with the desired AMI, so the playbook launches a EC2 instance
and creates a Security group with some special ports oppen for CircleCi software to run.


The problem here is that i need a enterprise trial of CircleCI to be able to end the instalation on the machine, actually im waiting for them to answer me with the key for the  enterprise trial.

Meanwile as i cant continue with the instalation on the ec2 instance, i configured in their cloud the circleCI to work with a mini HelloWorld in Django i FORKED from a public GIT repo.
  
I configured CircleCi to run tests when a change in TEST repo is made, it will run the django app and a basic ansibleplaybook. When the MASTER branch recieves a change it will run only the playbook.
The code is in .circleci/config.yml


STEPS: ( actually waiting for the enterprise trial to make it work on ec2, so i configured it on their cloud, its exactly the same )


1. In the git repo, you will find the ec2deploy.yml and hosts file, both required to execute the Ansble playbook to deploy a ec2 instance with a configured security group.
IMPORTANT:
 
 In order to make the ansibleplaybook you need to create a user in AWS and add this local variables and create access key for it, then add them as local variables:

 export AWS_ACCESS_KEY_ID=""
 export AWS_SECRET_ACCESS_KEY=""
 
 Install:
 
 sudo pip install --upgrade pip
 sudo pip install boto
 sudo yum install ansible
 sudo pip install boto3
 
 Execute:
 
 ansible-playbook -i ./hosts ec2instance.yml
 

2. I actually have the aws machine running, but with a security group that blocks the access, please send me  a message so i grant access.


3. Once you have access to the machine ( actually dont have the lisence ) you will see it asks for .rly file ( the trial for the enterprise )

So taking into account i cant end the conf on the aws machine, i continued on the web wich is exactly the same:

Go to:
https://circleci.com/vcs-authorize/ 

Log in with Bitbucket:
Add your bitbucket @user that I added on this Bitbucket project.


On the left side select PROJECTS and press Set Up Project:
test-onestick

The first time you set it up it will imediatly start running a test, you can see it on the Builds window.



4. The conf file of the circleCi is located at .circleci/config.yml:

This conf runs with Workflows and is configured to run diff workflows depending on the branch.
For the TEST branch i also made the second job depend on the first one so if the first one fails the second wont be executed.



