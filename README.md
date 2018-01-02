_Warning: This repository reflects the python client as of 0.8.0-beta release. The current release is 0.9.0-beta. There are **breaking changes** between these two releases and this client needs to be updated before it will work. If you are looking for a working client please see the [Javascript client repository](https://github.com/ethereum-alarm-clock/eac.js)._

# Alarm Client

The Python client to interact with the Ethereum Alarm Clock contracts.

## Requirements

The `ethereum-alarm-clock-client` python package requires some system
dependencies to install.  Please see the [pyethereum documentation](https://github.com/ethereum/pyethereum/wiki/Developer-Notes) for more
information on how to install these.

This package is only tested against Python 3.5.  It may work on other versions
but they are explicitly not supported.

This package is only tested on unix based platforms (OSX and Linux).  It may
work on other platforms but they are explicitly not supported.

## Installation

The ``ethereum-alarm-clock-client`` package can be installed using ``pip`` like this.

```
    $ pip install ethereum-alarm-clock-client
```

Or directly from source like this.

```
    $ python setup.py install
```

If you are planning on modifying the code or developing a new feature you
should instead install like this.

```
    $ python setup.py develop
```

## The `eth_alarm` executable

Once you've installed the package you should have the ``eth_alarm`` executable
available on your command line.

```
    $ eth_alarm
    Usage: eth_alarm [OPTIONS] COMMAND [ARGS]...

    Options:
      -t, --tracker-address TEXT      The address of the RequestTracker contract
                                      that should be used.
      -f, --factory-address TEXT      The address of the RequestFactory contract
                                      that should be used.
      --payment-lib-address TEXT      The address of the PaymentLib contract that
                                      should be used.
      -r, --request-lib-address TEXT  The address of the RequestLib contract that
                                      should be used.
      -l, --log-level INTEGER         Integer logging level - 10:DEBUG 20:INFO
                                      30:WARNING 40:ERROR
      -p, --provider TEXT             Web3.py provider type to use to connect to
                                      the chain.  Supported values are 'rpc',
                                      'ipc', or any dot-separated python path to a
                                      web3 provider class
      --ipc-path TEXT                 Path to the IPC socket that the IPCProvider
                                      will connect to.
      --rpc-host TEXT                 Hostname or IP address of the RPC server
      --rpc-port INTEGER              The port to use when connecting to the RPC
                                      server
      -a, --compiled-assets-path PATH
                                      Path to JSON file which contains the
                                      compiled contract assets
      --back-scan-seconds INTEGER     Number of seconds to scan into the past for
                                      timestamp based calls
      --forward-scan-seconds INTEGER  Number of seconds to scan into the future
                                      for timestamp based calls
      --back-scan-blocks INTEGER      Number of blocks to scan into the past for
                                      block based calls
      --forward-scan-blocks INTEGER   Number of blocks to scan into the future for
                                      block based calls
      --help                          Show this message and exit.

    Commands:
      client:monitor  Scan the blockchain for events from the alarm...
      client:run
      repl            Drop into a debugger shell with most of what...
      request:create  Schedule a transaction to be executed at a...
```

## Rollbar Integration

Monitoring these sorts of things can be difficult.  I am a big fan of the
[rollbar](https://rollbar.com/) service which provides what I feel is a very solid monitoring and
log management solution.

To enable rollbar logging with the ``eth_alarm`` client you'll need to do the
following.

1. Install the python rollbar package.
   * ``$ pip install rollbar``
2. Run ``eth_alarm`` with the following environment variables set.
   * ``ROLLBAR_SECRET`` set to the *server side* token that rollbar provides.
   * ``ROLLBAR_ENVIRONMENT`` set to a string such as `'production'` or `'ec2-instance-abcdefg'``.

_Please see `docs/cli.rst` for the rest of the documentation._