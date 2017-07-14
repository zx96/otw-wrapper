otw-wrapper
===========
This is a wrapper script for the wargames on http://overthewire.org.
Right now, it only supports the wargames that run over standard SSH.
It requires that the sshpass program be installed in order to pass saved
credentials to the SSH client. Please note that this program generally
should not be used, but I believe it's acceptable for a wargame like this.
It is also expected that you're running bash or zsh. I haven't tested this
with anything else, and I'm not planning on it. I'm more likely to remake
this as a Python script than bother supporting extra shells.

You can install it by issuing the following command in your shell:
(wget)
`wget -O ~/.otw https://raw.githubusercontent.com/zx96/otw-wrapper/master/otw`
(cURL)
`curl -o ~/.otw https://raw.githubusercontent.com/zx96/otw-wrapper/master/otw`

After that, you need to source it in your .bashrc or similar file:
(this has only been tested with bash and zsh)
`echo "source ~/.otw" >> .bashrc`

After you install it, you'll need to either start up a new shell or
manually run `source ~/.otw` in an existing shell.

The syntax for the script is `otw [level] [password]`.
For example, you can type `otw bandit0 bandit0` to log into the first level
of the Bandit wargame.
After you've successfully logged in once, the script will store the valid
password away in ~/.otwpass.
Once this happens, you can log in again anytime with just `otw [level]`.

If you want to set up WeChall (http://overthewire.org/about/wechall.html),
run `otw_setup_wechall` and type in your username and token.
The script will store your credentials in ~/.otwenv and that file will be
sourced by the script.

You can also run `otw_setup_persist` to create a persistent directory for use
across multiple logins into an OverTheWire server. The name is randomly
generated in order to make it difficult for others to steal the awesome exploits
you're going to end up developing for the challenges.

If you want to set up WeChall later on after doing a few levels, or if you
just forget to run wechall for a level, you can run `otw [level] wechall`
to log into the level and update WeChall.
Some levels (namely, those that don't just give you a shell, like bandit26)
break this, and you'll just have to connect and run wechall manually.

