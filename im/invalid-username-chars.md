# (in)valid characters in IM usernames

## XMPP:

Invalid characters in XMPP usernames:
* `U+0022` (")
* `U+0026` (&)
* `U+0027` (')
* `U+002F` (/)
* `U+003A` (:)
* `U+003C` (<)
* `U+003E` (>)
* `U+0040` (@)


## matrix/synapse:

Valid characters in matrix/synapse usernames:

```
"User ID can only contain characters a-z, 0-9, or '=_-./'"
```

Everything else is invalid.


## mattermost/model:

Valid characters in mattermost:

```
regexp.MustCompile(`^[a-z0-9\.\-_]+$`)
```

Everything else is invalid.
