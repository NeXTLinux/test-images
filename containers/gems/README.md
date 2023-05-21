# `lean`
This container was created initially to ensure parity in Nextlinux Engine analyzers with `gosbom` output. The idea is to make the resulting container
image as lean as possible.

This process means that some oddities are present like:

* Ruby packages are installed, but there is no Ruby interpreter present.
