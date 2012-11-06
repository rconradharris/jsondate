========
jsondate
========


Sick of rewriting the same JSON datetime handling code for each project?
``jsondate`` is a drop-in replacement for Python's standard ``json`` library that
adds sensible handling of ``datetime`` and ``date`` objects.

``jsondate`` uses ISO8601 for encoding ``datetime`` objects and the
date-specific part of ISO6801 for encoding ``date`` objects.

Example::

    import datetime
    import jsondate as json

    >>> data = json.dumps(dict(created_at=datetime.datetime(2012, 10, 31)))
    '{"created_at": "2012-10-31T00:00:00Z"}'

    >>> json.loads(data)
    {u'created_at': datetime.datetime(2012, 10, 31, 0, 0)}

    >>> date = json.dumps(dict(date=datetime.date(2012, 10, 31)))
    '{"date": "2012-10-31"}'

    >>> json.loads(data)
    {u'created_at': datetime.date(2012, 10, 31)}



Unicode Empty Strings
=====================

The ``json`` standard library module will return ``unicode`` objects for all
strings except empty strings, which are returned as ``str`` objects.

This inconsistency can be annoying when using libraries that expect all input
to be ``unicode``.

``jsondate`` fixes this by returning empty-strings as ``unicode`` objects as
well.
