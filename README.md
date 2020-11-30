## UDP to TCP DNS Forwarder

`ttdnsd` is a daemon that can forward UDP DNS requests to a TCP DNS server. It is typically run as a local DNS server which forwards request to another DNS server via TCP, because many systems don't support DNS resolver entries that use TCP or a different port.

This is a fork of `ttdnsd` "The TOR TCP DNS Daemon" by Collin Mulliner: http://www.mulliner.org/collin/ttdnsd.php

This fork fixes compatibility issues on non-Linux systems and allows specification of custom port both on the listening side as well as the resolver (peer) side.

I have not modified the `Makefile`, so on macOS you may want to use simply

    clang -o ttdnsd main.c

instead of `make`.

### Usage

```
$ ttdnsd -h

 Usage: ttdnsd [bfprcdl]

	-b	<local ip>	bind to local ip
	-f	<dns file>	filename to read dns server ip(s) from
	-p	<port>		UDP port to bind to (53)
	-r	<port>		TCP port to connect to on the resolver (53)
	-c			DON'T chroot(2) to /var/run/ttdnsd
	-d			DEBUG don't fork/chroot and print debug
	-l			don't write debug log (ttdnsd.debug)
```
