
`.nlzrc` is an optional JSON configuration file for local environments.
It's completely optional.
You may have a global, `.nlzrc` configuration for your computer as well as local `.nlzrc` configuration for each app.
For example, you might want to point all your requests to a proxy on your network instead of https://nlz.io.

### .proxy and .self-signed

```json
{
  "proxy": "localhost:8888",
  "self-signed": true
}
```

This is to set a custom proxy other than https://nlz.io.
`proxy` should be the full host, including the port.
Set `self-signed` to `true` if the proxy is using a self-signed certification,
otherwise an error will be thrown.
Remember, proxies must always use SSL.

### .directory

```json
{
  "directory": "/User/jong/.repositories"
}
```

By default, all files are stored to `process.cwd() + '/repositories'`.
Thus, every app or component you work on will have its own `directory` folder.
This may be less than ideal for you as you'll have multiple copies.

You may optionally set this directory to a global directory like `~/.repositories`
so that every app or component you work on share the same files.
It will also make installations a little faster.

### .transforms

Options for transforms.
__All__ transforms are enabled by default.
If you set any `.transforms` options,
all transforms will now be opt-in.

You shouldn't need to touch this as transforms' libraries are lazily loaded.
You won't get much performance benefit from disabling transforms.

### .entrypoints

The entry points for the build.
This allows you to not specify the entry points every time you run `nlz build(1)`.

```json
{
  "entrypoints": ["client/index.js", "client/index.css"]
}
```

You may also use objects if you want to set custom options on each entry point:

```json
{
  "entrypoints": {
    "client/index.js": {

    },
    "client/index.css": {

    }
  }
}
```
