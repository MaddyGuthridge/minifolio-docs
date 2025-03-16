# Minifolio's data format

## Public data


Central to Minifolio is its public data. This is the data that is used to generate the website contents. This data can optionally be backed up using the Git tools in the admin panel, but since it is just a directory with files, you can use any other backup method you desire.


Minifolio will store public data in the directory defined by the `DATA_REPO_PATH` environment variable. For example, the recommended Docker Compose configuration mounts the data directory as a volume at `/data`.


The data is comprised of a hierarchy of item directories, where any directory with an `info.json` file is considered to be an item. The top-level directory is the root item, which cannot be moved or deleted. It also contains a `config.json` which contains the public site configuration, which is used to control things such as external site verification.


All files inside of the public data are publicly viewable. You should ***NOT*** store sensitive or private information in this directory.


### Items


Each directory is considered to be an item if it has an `info.json` file. This file contains basic metadata for the item, such as its display name.


Items can be infinitely nested, so directories within another item directory are considered to be child items if they have their own `info.json`. Item directories inside of directories without an `info.json` are not considered to be items, as all items (except for the root item) must have a valid parent item.


## Private data

The private data is used to store private configuration and secrets. Minifolio will store private data in the directory defined by the `PRIVATE_DATA_PATH` environment variable. For example, the recommended Docker Compose configuration mounts the data directory as a volume at `/private_data`.

### `config.local.json`

Contains the local configuration of the server, including credentials and token
info.


### Keys directory


Contains keys and other information required for Minifolio to perform SSH operations.


* `known_hosts`: similar to `~/.ssh/known_hosts`. Minifolio will only download host info for the hosts it specifically connects to
* `id_ed25519` and `id_ed25519.pub`: Minifolio's SSH key, if you aren't using the system SSH. These are used when performing git operations.

### `auth.secret`

Contains the authentication secret used by the server. This is used to validate
JWTs. Currently, this secret cannot be reset using the front-end. If you wish to reset it, you will need to run `tr -dc A-Za-z0-9 </dev/urandom | head -c 21 > private_data/auth.secret` then restart Minifolio.

