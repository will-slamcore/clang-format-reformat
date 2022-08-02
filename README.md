clang-format-reformat
============================

This script is designed to help SLAMcore developers who use git with rebasing
their local changes after the repository-wide formatting conversion

This is based on the MongoDB clang_format.py script[1] explained in [2].  Many
thanks to the MongoDB project for providing the original script.

Instructions
============

After the tree-wide conversion planned to happen on 5th of Aug 2022, you can
follow the following steps in order to rebase your local changes on top of the
reformatted tree.

  * Clone this repository somewhere on your local disk.
  * Install the requirements (using a virtual environment if you wish):

    `   pip install -r requirements.txt`


  * With the branch you want to be updated checked-out,
  run the following commands in the root of the repository to be formatted:

    ```sh
      git fetch
      /path/to/clang-format-reformat/clang_format.py
    ````

  * Check any errors such as `Please rebase to ...`

This command first makes a few checks in the environment to ensure that everything
is right and if not shows prompts about what went wrong and after that starts
the rebase process.

If you start running this command on git branch called "foo", this command will
save its result on a new git branch called "foo-reformatted" and will check
it out when it's finished.  It will not modify the original "foo" branch in any
way, so it is not destructive.  If you're happy with the results, you may run
the following commands to make the results permanent:

  * `git checkout foo`
  * `git reset --hard foo-reformatted # make sure the local directory is unmodified!!!`


References
==========

* [1] https://github.com/mongodb/mongo/blob/master/buildscripts/clang_format.py
* [2] https://engineering.mongodb.com/post/succeeding-with-clangformat-part-3-persisting-the-change
