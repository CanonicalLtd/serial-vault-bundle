# A scalable Serial Vault bundle

This bundle deploys the Serial Vault, an assertion signing service for [Ubuntu Core](https://www.ubuntu.com/core).
The application provides a signing service and an admin user interface, both behind a haproxy load balancer.

# Usage

You can deploy the single bundle with:

    juju deploy serial-vault-bundle

After deployment you need to expose the services, either via the GUI or the CLI:

    juju expose haproxy

Then run a `juju status haproxy` to get the public address. The browse to that http://\<address\>:8081 in your browser to configure the services.

## Scale out usage

You can add and remove more serial-vault instances to horizontally scale:

    juju add-unit serial-vault
    juju add-unit serial-vault-admin

This can be done without service interruption.

Typically, the services would have an apache frontend that would provide SSL connections, and the admin service would be restricted to your own internal network.
