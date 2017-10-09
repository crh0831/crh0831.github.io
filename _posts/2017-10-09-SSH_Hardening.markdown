---
layout: post
title: SSH Hardening  
date:  Mon 09 Oct 2017 01:52:05 PM EDT
categories: howto
---

## Summary

It's about time I get a standard sshd_config file that doesn't rely on sane defaults.

## Disabling Password-based Authentication

... you should disable password-based authentication altogether. Make sure to only do this once you have verified that
you can log in with an account that can
escalate to root - or that you have an alternate way of getting back onto your machine. To lock down your server, edit
your /etc/sshd/sshd_config and set the
following options:

        Protocol 2
        PermitRootLogin without-password
        PubkeyAuthentication yes
        ChallengeResponseAuthentication no
        PasswordAuthentication no
        UsePAM yes

This sets a fairly strict set of defaults that should make most bots give up right after connecting. The options we used
were:

**Protocol**
Verify that only protocol version 2 is allowed. There's no point in supporting the rather dated version 1 and you're
only opening yourself up to ye olde bugs
of old. If this reads 1 or 1,2, change it to just 2.

**PermitRootLogin**
The setting `without-password` is a bit of a misnomer. What that does is it enables root logins, but only if the
mechanism to authenticate was not a password -
i.e. it enables root logins, but only for public key authentication. This is good. Never set this to yes.

**PubkeyAuthentication**
Make sure this is set to yes, otherwise you won't be able to log in once you disable passwords.

**ChallengeResponseAuthentication**
Set this to no to disable non-pubkey logins that could otherwise be handled through PAM.

**PasswordAuthentication**
This is what we were here for: set this to no to disable tunneled clear text passwords.

**UsePAM**
If your system has PAM set up, it'll still be a good idea to keep this enabled even if you disabled password-based
authentication. This is because PAM also
provides session and account management, so set this to yes.
All you need to do now is restart the SSH server, like so:

        /etc/init.d/ssh restart

Note that restarting SSH will not kill your active session, so you should verify that the new settings will actually let
you log in before closing your
current session - and revert and restart SSH again if they don't.

For maximum effect, make sure that SSH is the only way to log on to your server. At the very least make really certain
that you don't have telnet enabled!
There, now you're all set and can be very confident that bots won't be able to access your machines through SSH

---

Reference(s):

* [How to Harden SSH with Identities and Certificates](https://ef.gy/hardening-ssh)
