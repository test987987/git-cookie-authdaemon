# Git authentication tools for Google Compute Engine

The `git-cookie-authdaemon` uses the GCE metadata server to acquire an
OAuth2 access token and configures `git` to always present this OAuth2
token when connecting to googlesource.com or
[Google Cloud Source Repositories][CSR].

[CSR]: https://cloud.google.com/source-repositories/

## Setup

Launch the GCE VMs with the gerritcodereview scope requested, for example:

```
gcloud compute instances create \
  --scopes https://www.googleapis.com/auth/gerritcodereview \
  ...
```

## Installation

Install the daemon within the VM image and start it running:

```
sudo apt-get install git
git clone https://gerrit.googlesource.com/gcompute-tools/
./gcompute-tools/git-cookie-authdaemon
```

The daemon launches itself into the background and continues
to keep the OAuth2 access token fresh.
