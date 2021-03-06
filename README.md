Tools useful for maintaining and updating conda recipes and packages.

Recipe tools
------------

* `sync_cf` : Rebase feedstocks against conda-forge
* `update_recipe` : Update a recipe to a specific version
* `prepare_batch_file` : Prepare a batch-file.txt for submission to c3i batch
* `create_clobber` : Create recipe_clobber.yaml files
* `show_git_messages` : Print out git messages for a set of feedstocks.
* `push_feedstock_changes` : Push up changes for a set of feedstocks.

Package tools
-------------

* `extract_index_json`
* `replace_index_json`

Misc tools
----------
* `gh` : Open a GitHub repository in the current web browser.
* `pypi` : Open a PyPI package page in the current web browser.
* `reqs` : Attempt to list packages dependencies from PyPI.
* `find_outdated_packages_pypi.py` : Find outdated packages on a Anaconda.org channel.


Suggested workflow
------------------

Prepare and run a series of builds on concourse.

* Prepare of list of outdated feedstocks.
* Run `sync_cf` to rebase the feedstocks against conda-forge.
* Run `update_recipe` for each outdated feedstock.
* Run `prepare_batch_file` to create a batch-file.txt file.
* Run `create_clobber` to create recipe clobber files for each feedstock.
* Submit builds to c3i using `c3i batch batch-file.txt` 

Once these builds are finished and have been added to the package reposistory.

* Run `show_git_messages` to prepare a set of git commit messages.
* Run `push_feedstock_changes` to push the feedstock changes to GitHub.
* Add changed feedstocks submodules and push to aggregate.


ToDo
----

Rewrite these tools as a Python library with entry points for better re-use.

The following tools would be nice to have:

* `kick_builds` : restart builds
* `summarize_builds` : give a summary of builds
* `check-artifacts` : Scan artifacts for completeness and issues
* `copy-artifacts` : Copy artifacts from pipelines into the package location.
