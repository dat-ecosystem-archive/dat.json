# dat.json

The WIP specification for the dat.json meta format.

## Specification

Add a `dat.json` with any of those keys - all are optional - to the root of a dat archive to help tooling work with your archive more nicely:

```json
{
  "name": "A human friendly name",
  "author": "Author name with optional <email>"
}
```

## Support

- [Dat-Desktop](https://github.com/juliangruber/dat-desktop) will use `.title` to display a nice archive name instead of just its key
