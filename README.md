guard-autoupload
================

Autoupload plugin used for uploading all local changes to remote host.
Uses either SFTP or FTP.

Usage
-----

Sample guardfile:

    opts = {
        :protocol => :scp,        # Protocol used to connect to remote host.
                                  # Possible values are :scp, :sftp and :ftp.
                                  # Of these :scp is the preferred one for
                                  # its stability.
        :host => "remote_host",
        :user => "username",
        :password => "password",
        :remote => "remote_path",
        :verbose => false,        # if true you get all outputs
        :quiet => false           # if true outputs only on exceptions.
    }

    guard :autoupload, opts do
        watch(/^((?!Guardfile$).)*$/)
        # Matches every other file but Guardfile. This way we don't
        # accidentally upload the credentials.
    end

Dependencies
------------

 - guard
 - Net::SFTP
 - Net::SSH::Simple

Installation
------------

For now you need to install `guard-autoupload` by building the gem manually
and installing from that:

    gem build guard-autoupload.gemspec
    gem install guard-autoupload-0.3.gem

Author
------

This guard plugin was written by Jyrki Lilja and is used at FocusFlow.
The code is hevily based on [vincenthu's guard-flopbox][gsftp] and
[bgarret's guard-ftpsync][gftp].

[gsftp]: https://github.com/vincentchu/guard-flopbox
[gftp]: https://github.com/bgarret/guard-ftpsync

