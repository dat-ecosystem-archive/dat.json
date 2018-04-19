# dat.json

The WIP specification for the dat.json meta format.

```json
{
  "title": "My paper library",
  "author": "Julian Gruber <julian@juliangruber.com>",
  "url": "dat://c75ffb161a9965e47323ba9b76aa11f649504b0d2d5d062dcb3438d5aeadc187",
  "links": {
    "license": [{"href": "http://creativecommons.org/licenses/by-nc/2.5/", "title": "CC BY-NC 2.5"}]
  }
}
```

## Specification

Add a `dat.json` with any of those keys - all are optional - to the root of a dat archive to help tooling work with your archive more nicely:

### `.title`

A short but descriptive human friendly title.

### `.description`

A one- or two-line description of the archive.

### `.url`

Url of the Dat archive. This will usually be the `dat://` then the archive key.

### `.author`

The archive's author - the packager, not necessarily the data's author as well. Can be either an object with any of those keys:

```json
{
  "name": "Julian Gruber",
  "email": "julian@juliangruber.com",
  "web": "https://juliangruber.com"
}
```

or a string with at least the name and any of the segments email and web:

```js
"NAME <EMAIL> (WEB)"
```

like for example:

- `"Julian Gruber"`
- `"Julian Gruber <julian@juliangruber.com>"`
- `"Julian Gruber (https://juliangruber.com/)"`
- `"Julian Gruber <julian@juliangruber.com> (https://juliangruber.com/)"`

### `.links`

An object containing a set of Web links from the Dat. It is a mapping of "rel" values to arrays of link objects, as follows:

```json
{
  "rel-type": [{"href": "https://.../"}]
}
```

The `.links` follows the same schema as [Web links](https://www.w3.org/TR/html5/document-metadata.html#the-link-element) and so any attribute which applies to a `<link>` will apply to these values. The one difference is how the `rel` value is handled: in this field, the `rel` is used as the key of the `links` map. Only one `rel` value should be used. If a link has additional rel values, it can specify them using the `rel` field on the link object. For instance, a link with the `rel` value of `"foo bar baz"` would look like this:

```json
{
  "foo": [{"href": "https://.../", "rel": "bar baz"}]
}
```

Links can be duplicated, and so it would also be possible to handle this case with 3 different link objects:

```json
{
  "foo": [{"href": "https://.../"}],
  "bar": [{"href": "https://.../"}],
  "baz": [{"href": "https://.../"}],
}
```

## Support

- [Dat-Desktop](https://github.com/juliangruber/dat-desktop) will use `.title` to display a nice archive name instead of just its key
