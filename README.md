# passd - Forward Your _pass_ Passwords Over SSH

_passd_ and _passc_ combine to let you access your
[_pass_](http://www.passwordstore.org/) passwords on remote servers via SSH port
forwarding.

## Usage

On your local workstation, run

    passd

Edit your .ssh/config for the remote host and add

    RemoteForward 8739:localhost:8739

On the remote server, run

    passc PASS_OPTIONS

_passc_ accepts any argument that _pass_ does. It also has bash completion.

## Security Concerns

_passd_ works by running a thin server on your workstation (listening on
localhost) and forwarding requests over an SSH-remote-forwarded port. This means
any user on the local system or the remote system can access your passd server.
__DO NOT FORWARD PORTS TO MULTI-USER OR UNTRUSTED SERVERS.__

Other than that, access to your local password store will go through your local
gpg-agent setup, and you'll need a graphical pinentry program set up.  
On OS X, I think this means using GPGTools not the homebrew version of
gpg-agent.

In order to prevent a local or remote attacker from plundering your passwords,
we force gpg-agent to drop all stored passphrases before running `pass`. If you
use other keys with gpg-agent this will get annoying. Pull requests welcome.

## Installation

### Requirements

`passd` requires `socat` and `pass` (available in apt-get and brew)

`passc` requires `nc` aka netcat (available in apt-get and brew)

### Manual Installation

    git clone https://github.com/werkshy/passd
	cd passd
	cp bin/* /usr/local/bin
	cp bash_completion.d/* /etc/bash_completion.d

### Installation via [_bash-get_](https://github.com/werkshy/bash-get)

	bash-get install github.com/werkshy/passd

