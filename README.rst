+++++++++++
soloprocess
+++++++++++

I finally got around to making code from this blog post into a package::

    http://blog.tplus1.com/blog/2012/08/08/python-allow-only-one-running-instance-of-a-script/

Say you start a cron job every hour, and each time, the job runs for
about 20 minutes.  But every once in a while, the job runs for 90
minutes, or even 12 hours.

And in those cases, you don't want to start another redundant cron job,
because the first one is still running.

That's what I wrote this for.

Install like this::

    $ pip install soloprocess

Here's how to use it::

    >>> import soloprocess

    >>> soloprocess.write_pidfile_or_die("/tmp/process-one.pid")
    '/tmp/process-one.pid'

    >>> soloprocess.write_pidfile_or_die("/tmp/process-one.pid") # doctest: +ELLIPSIS
    Traceback (most recent call last):
    ...
    ProcessAlreadyRunning: Sorry, found a pidfile!  Process ... is still running.
