# Munin plugins for Bitcoin Core

## Installation & Configuration

1. Copy the `bitcoind_*` scripts to `/etc/munin/plugins`.

1. If you're using SELinux, don't forget to `chcon` them properly.

1. Configure the plugins by creating a file named `/etc/munin/plugin-conf.d/bitcoind` with this content:

    ```
	[bitcoind*]
	user bitcoin
	env.binary bitcoin-cli
	env.conf_dir /home/bitcoin/.bitcoin
	env.data_dir /mnt/data/bitcoin

    ```

    This will tell Munin to run `bitcoin-cli` as the `bitcoin` user. Adapt it to your setup and avoid using `root`.
	`conf_dir` is the path to bitcoin.conf folder, `data_dir` is path to a possibly different blockchain data dir.

1. Restart the *munin-node* daemon with `systemctl restart munin-node` or `/etc/init.d/munin-node restart`.

1. Done. You should now start to see a new section *bitcoind* in your Munin pages with the corresponding graphs.

## License

AGPLv3+

