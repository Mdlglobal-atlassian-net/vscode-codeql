Visual Studio Code Extension for QL
===

Configuration
---

### Setting the path to Semmle Core

For IntelliSense and query evaluation to work, you must configure the path to a Semmle Core distribution. This is done by setting the `ql.distributionPath` setting in your VS Code settings to point to your distribution. If you have built your own distribution from a `Semmle/code` checkout, this path will be something like `codeRoot/target/intree/standard`, where `codeRoot` is the root of your `Semmle/code` checkout.

You can also download the release Semmle Core (odasa) from the corporate [release downloads webpage](https://wiki.semmle.com/display/REL/QL+tools+downloads).

This setting can be set per-workspace, or you can set it in your
global user settings to apply to all workspaces you open.

### Configuring a QL project

* Create project configuration file. Suppose your working directory is called `~/js-queries`.
Then you can make a file `~/js-queries/.vscode/settings.json` with contents
```json
{
  "ql.projects": {
    ".": {
      "dbScheme": "jslib/semmlecode.javascript.dbscheme",
      "libraryPath": ["jslib"]
    }
  }
}
```
and copy contents of the `Semmle/code/ql/javascript/ql/src` to `~/js-queries/jslib`.

Using
---

### Interface

The contributed commands to the command palette (default `Ctrl+Shift+P`) are:

|Command|Comment|
|---|---|
|QL: Choose Database|Choose a database to work with|

A valid database in the context of this QL plugin is a directory containing the database folder.
Here is an example of a directory produced as a revision using `odasa bootstrap` command:

```
revision-2019-June-28--10-38-01
├── external
│   ├── data
│   ├── defects
│   ├── metrics
│   └── trap
├── log
├── output
│   ├── extra-data
│   └── results
│       └── semmlecode-python-queries
└── working
    ├── db-python
    │   └── default
    └── trap
        └── externalArtifacts
```

In the context of QL for VSCode plugin, the `working` directory would be the database folder
that you would have to browse to.

The `QL` view should exist on the left, below explorer, version control, extensions, etc. icons.
Within that panel you should be able to see a list of databases.