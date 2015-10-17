# chef-repo-splunk

A chef repo for Splunk Enterprise cluster provisioning including all required roles and dependent cookbooks.

## Cookbooks
* chef-splunk (= 1.4.0)
* chef-vault (~> 1.3.1)

## Roles

### Note about cookbooks packaging:
Required cookbooks are listed in Berksfile instead of duplicating them in this repo.
A single archive containing all required cookbooks can be easily created using `Berkshelf`.
This generated cookbooks archive is included in the repo as berks-package.tar.gz for convenience.

Whenever changing Berkshelf file, you need to update the cookbooks archive as follows:

    $ cd <>/chef-splunk-repo
    $ berks package berks-package.tar.gz

The archive can be:
* extracted and uploaded to a Chef Server, or
* extracted and provided to chef-solo using `cookbook_path` config, or
* extracted and provided to chef-client in local mode along with this repo using `chef_repo_path` config







