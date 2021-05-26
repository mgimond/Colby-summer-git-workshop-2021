### Configure your global Git environment

If you haven't used Git on your computer yet, you will need to configure a few settings: Your name and your contact information (email address). This info is used to keep track of the author behind any changes made to a Git repository. This is not necessarily tied to an existing account, you can assign and name/email address you see fit.

Type the following while replacing `Jane Doe`  and `jdcolby@colby.edu` with  your name and email address respectively.  (Do not type the `$` character! This is only referencing the existing prompt in your terminal).

```bash
$ git config --global user.name 'Jane Doe'
$ git config --global user.email 'jdcolby@colby.edu'
```

To check your settings, type:

```bash
$ git config --global --list
```
You should see something like:
   <pre>
   user.name=jdcolby
   user.email=jdcolby.com
   </pre>
