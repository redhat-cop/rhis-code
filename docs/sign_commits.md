# Sign git commit

This document explains how to sign commits in Git and VSCode. Signing,
or code signing specifically, is the process of using cryptography to
digitally add a signature to data. The receiver of the data can verify
that the signature is authentic, and therefore must’ve come from the
signatory.

It is mainly required to configure a few settings, namely `user.email`
and `user.name`.

    # git config --global user.email "name@domain.net"
    # git config --global user.name "Name Surname"

When you authenticate with the version control system, Git would not
care much about the commits. When you authenticate to push to remote
repositories, you’re authenticating to do just that– push changes. The
commits don’t require authentication regardless of who authored or
committed them. In that case, anyone can use this settings and there is
Commit Signing exist to avoid this situation.

GNU Privacy Guard (GnuPG or GPG) allows you to create cryptographic
asymmetric key pairs that can be used for the encryption and signing of
data. They consist of a public and private key.

## How to Sign Commits in Git

### Set up GPG

First you have to install GPG, if you don’t already have it. You can
verify your installation

    # gpg --version

### How to Generate GPG Keys

If you already have a GPG key, you can skip this step. It’s perfectly
fine to reuse GPG keys.

You can get a list of your GPG keys with:

    # gpg --list-keys

If you already have gpg keys, import them to use.

    # gpg --import public.key
    # gpg --import private.key

The following command will start an interactive script that will ask
questions.

    gpg --full-gen-key

1.  For what kind of key you want, input 1 which is "RSA and RSA".

2.  For key size, input 4096. This is the minimum size for GitHub and
    GitLab, and the maximum size GPG will let us generate.

3.  For how long the key should last, use whatever suits you. The
    default is 0, which means to never expire.

4.  Verify the information is correct by inputting y.

5.  GPG will ask for personal information which is stored in your key.

    1.  Your name, this can be anything at least 5 characters in length.

    2.  Your email address, use an email you plan to commit with. You
        must’ve verified this email on the remote account you’ll push
        with.

    3.  A comment, you can type whatever, or press enter to leave it
        blank.

6.  Verify the information is correct by inputting o.

GPG will ask for a passphrase to protect the key and then will start
generating keys.

### How to Export GPG Keys

You need to export the public-key so you can upload it to GitHub. We use
the --armor argument to indicate that we want to export it in an ASCII
armored format instead of binary. This writes the public-key to a file
named gpg-key.pub.

    # gpg --export --armor A335545C5A15E29D991737510D1FCF36E72F438E > ./gpg-key.pub

!!! tip

    Don’t forget to backup your passphrase and gpg keys!

## Enable GPG Signing

Add your signing key to your commits.

    # git config user.signingkey A335545C5A15E29D991737510D1FBF36E72F438E

Then to enable signing all commits, set the `commit.gpgsign` setting
using git config.

    # git config --global commit.gpgsign true

Finally you have to tell VSCode to append the `-s` flag to the git
commit command, to use signed committing now. Open the settings, search
for “gpg” and check the box “Enables commit signing with GPG”.

## Set up GitHub

Now you have to give GitHub (or whatever version control system you’re
using) your public key. We’ll need the exported public-key for the
following steps, so open the gpg-key.pub file in any editor like VSCode,
and copy the contents to your clipboard.

On GitHub, you can go to your `settings`, under `SSH and GPG keys`, then
click `New GPG key`. Paste the contents of gpg-key.pub into the Key
field on GitHub, and click `Add GPG key`.

Now you’re able to make signed commits to your repositories!
