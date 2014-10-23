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

## Installation

### Manual Installation

    git clone https://github.com/werkshy/passd
	cd passd
	cp bin/* /usr/local/bin
	cp bash_completion.d/* /etc/bash_completion.d

### Installation via [_bash-get_](https://github.com/werkshy/bash-get)

	bash-get install github.com/werkshy/passd

