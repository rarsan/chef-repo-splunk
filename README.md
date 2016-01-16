# Chef Repository for Splunk Enterprise

A Chef repo for Splunk Enterprise cluster provisioning including all required roles and dependent cookbooks.

Placeholder nodes are also provided in case you use Chef local mode. These node files can act as your inventory list: keep the nodes that correspond to your existing or desired Splunk deployment and update their attributes (i.e. 'ipaddress', 'fqdn') to match your environment.

## Cookbooks
* chef-splunk (= 1.4.0-rarsan.1)
* chef-vault (~> 1.3.1)

## Roles
* `splunk_server`: Generic Splunk Enterprise configuration (used for standalone deployment)
* `splunk_cluster_master`: Cluster Master configuration in indexer cluster
* `splunk_cluster_search_head`: Search Head configuration in indexer cluster
* `splunk_cluster_peer`: Peer configuration in indexer cluster

## Nodes
* `cluster-master.json`: Cluster Master node (for chef local mode)

### Note about cookbooks packaging:
Required cookbooks are listed in Berksfile instead of duplicating them in this repo.
A single archive containing all required cookbooks can be easily created using `Berkshelf`.
This generated cookbooks archive is included in the repo as berks-package.tar.gz for convenience.

Whenever changing Berkshelf file, you need to update the cookbooks archive as follows:

    $ cd <>/chef-splunk-repo
    $ berks update
    $ berks package berks-package.tar.gz

The archive can be:
* extracted and uploaded to a Chef Server, or
* extracted and provided to chef-solo using `cookbook_path` config, or
* extracted and provided to chef-client in local mode along with this repo using `chef_repo_path` config

## Release Notes

* v0.7: Remove secret in data bag, and update Chef cookbook to use Splunk binaries 6.3.2 (1.4.0-rarsan.4)
* v0.6: Update Chef cookbook version to use Splunk binaries 6.3.1 (1.4.0-rarsan.3)
* v0.5: Update Chef cookbook version for custom `SPLUNK_DB` path support (1.4.0-rarsan.2)
* v0.4: Add placeholder Chef node for Cluster Master (applicable for chef local mode only)
* v0.3: Update Chef cookbook version for default SSL certs support (1.4.0-rarsan.1)
* v0.2: Set cookbooks versions (chef-splunk 1.4.0, chef-vault 1.3.1)
* v0.1: Initial release

