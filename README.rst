
FIRST PART OF THE TEST:
=======================
For the first part of the test I had to studdy the different tools that i could use for CI, not being able to use Attlasian tools.

When I started the first tools i thought that could match the team workload where:
    + Travis CI
    + CircleCI 
    + Jenkins

Lets have a closer look at each one:
----- TravisCI:
   PROS:
This tool is based on cloud solution, and runs over docker to execute the tests. 
One of the strong sides of TravisCI i consider is that it supports build matrix, allowing you to run test with different versions of the same lenguaje at the same time.
   CONS:
Well travisCi also has some bad things, it has no free enterprise plan, and prices are quite expensive, and for me one of the worst things it has is that there are not too many 3rd partys that support it.

------ CircleCI:
CircleCI and TravisCI are quite similar.
    PROS:
CircleCI is also cloud Base but it offers the chance to run it on cloud or on your own datacenter. ( But need to ask for the enterprise free trial and takes one day minimun, this slowed me down a little bit )
CircleCI also runs over docker to execute tests.
It also alows you to connect via ssh to the dockers running for a more in depth search of the problem.
    CONS:
It dosent support a great amount of programing lenguajes.


----- Jenkins:
Jenkins whas also one of the solutions i could aproach, but i wanted to test something different, and Jenkins requires a big configuration that may take longer to make it work properly.


So alfter this little ressume, i thought that the best tool whas CircleCI, the user interface looked very friendly and its high customizable. One of the biggest reason i thought that CircleCI 
will be better than TravisCI is that its supported by much more 3rd partys and this will alow the project to grow with many more chances.


SOLUCION:




RUN HELLOWORLD PROJECT:


A Django 'hello world' example.

For run this example need to install Django
framework execute the follow command::

    $ sudo pip install -r requirements.txt

And later followed by::

    $ python manage.py migrate

At which point you should see::

    Operations to perform:
      Apply all migrations: admin, contenttypes, sites, auth, sessions
    Running migrations:
      Rendering model states... DONE
      Applying contenttypes.0001_initial... OK
      Applying auth.0001_initial... OK
      Applying admin.0001_initial... OK
      Applying admin.0002_logentry_remove_auto_add... OK
      Applying contenttypes.0002_remove_content_type_name... OK
      Applying auth.0002_alter_permission_name_max_length... OK
      Applying auth.0003_alter_user_email_max_length... OK
      Applying auth.0004_alter_user_username_opts... OK
      Applying auth.0005_alter_user_last_login_null... OK
      Applying auth.0006_require_contenttypes_0002... OK
      Applying auth.0007_alter_validators_add_error_messages... OK
      Applying sessions.0001_initial... OK
      Applying sites.0001_initial... OK
      Applying sites.0002_alter_domain_unique... OK

After which you can run::

    $ python manage.py runserver

And open the following URL in your web browser:

 - http://127.0.0.1:8000/

And you can see the hello world example like this :

.. figure:: https://github.com/django-ve/helloworld/raw/master/docs/django_helloword.png
   :width: 332px
   :align: center
   :alt: A Django 'Hello World' example

A Django 'Hello World' example