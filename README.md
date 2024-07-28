<div align="center">

![logo](src/img/logo-b.png)

# backage

## Supplement the API

With a [JSON Endpoint](#endpoint) backed by a [SQLite Dataset](#database)

</div>

---

Is the Packages API missing something you need? Did you ever wish you could show info about packages as badges? Now you can get what you need! If you're here to make a badge, use something like [shields.io/json](https://shields.io/badges/dynamic-json-badge) and [these parameters](#url).

### Example

Here's what the badges could look like for [pihole-speedtest](https://github.com/arevindh/pihole-speedtest):

[![downloads/all](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fraw.githubusercontent.com%2Fipitio%2Fbackage%2Fmaster%2Findex%2Farevindh%2Fpihole-speedtest%2Fpihole-speedtest.json&query=%24.downloads&logo=github&label=downloads)](https://github.com/arevindh/pihole-speedtest/pkgs/container/pihole-speedtest) [![downloads/month](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fraw.githubusercontent.com%2Fipitio%2Fbackage%2Fmaster%2Findex%2Farevindh%2Fpihole-speedtest%2Fpihole-speedtest.json&query=%24.downloads_month&logo=github&label=month)](https://github.com/arevindh/pihole-speedtest/pkgs/container/pihole-speedtest) [![downloads/week](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fraw.githubusercontent.com%2Fipitio%2Fbackage%2Fmaster%2Findex%2Farevindh%2Fpihole-speedtest%2Fpihole-speedtest.json&query=%24.downloads_week&logo=github&label=week)](https://github.com/arevindh/pihole-speedtest/pkgs/container/pihole-speedtest) [![downloads/day](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fraw.githubusercontent.com%2Fipitio%2Fbackage%2Fmaster%2Findex%2Farevindh%2Fpihole-speedtest%2Fpihole-speedtest.json&query=%24.downloads_day&logo=github&label=day)](https://github.com/arevindh/pihole-speedtest/pkgs/container/pihole-speedtest) [![size](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fraw.githubusercontent.com%2Fipitio%2Fbackage%2Fmaster%2Findex%2Farevindh%2Fpihole-speedtest%2Fpihole-speedtest.json&query=%24.size&logo=github&label=size&color=a0a)](https://github.com/arevindh/pihole-speedtest/pkgs/container/pihole-speedtest) [![versions](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fraw.githubusercontent.com%2Fipitio%2Fbackage%2Fmaster%2Findex%2Farevindh%2Fpihole-speedtest%2Fpihole-speedtest.json&query=%24.versions&logo=github&label=versions&color=0a0)](https://github.com/arevindh/pihole-speedtest/pkgs/container/pihole-speedtest) [![releases](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fraw.githubusercontent.com%2Fipitio%2Fbackage%2Fmaster%2Findex%2Farevindh%2Fpihole-speedtest%2Fpihole-speedtest.json&query=%24.tagged&logo=github&label=releases&color=0a0)](https://github.com/arevindh/pihole-speedtest/pkgs/container/pihole-speedtest) [![latest](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fraw.githubusercontent.com%2Fipitio%2Fbackage%2Fmaster%2Findex%2Farevindh%2Fpihole-speedtest%2Fpihole-speedtest.json&query=%24.version%5B%3F(%40.tags.indexOf(%22latest%22)!%3D-1)%5D.tags%5B%3F(%40!%3D%22latest%22)%5D&logo=github&label=latest&color=0a0)](https://github.com/arevindh/pihole-speedtest/pkgs/container/pihole-speedtest) [![newest](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fraw.githubusercontent.com%2Fipitio%2Fbackage%2Fmaster%2Findex%2Farevindh%2Fpihole-speedtest%2Fpihole-speedtest.json&query=%24.version%5B%3F(%40.newest%3D%3Dtrue)%5D.name&logo=github&label=newest&color=0a0)](https://github.com/arevindh/pihole-speedtest/pkgs/container/pihole-speedtest)

### Endpoint

Refreshed several times a day, the endpoint is always in sync with the continually updated database. To add any users or orgs post-haste, you can either:

* open an issue, or
* add the case-sensitive name of each one on a new line in `owners.txt` on your own fork [here](https://github.com/ipitio/backage/edit/master/owners.txt) and make a pull request. Please add just the name, don't worry about slashes or anything.

#### URL

Replace `<OWNER>`, `<REPO>`, and `<PACKAGE>` with their respective values:

```markdown
https://raw.githubusercontent.com/pgoslatara/backage/master/index/<OWNER>/<REPO>/<PACKAGE>.json
```

#### JSONPath

Just fill in the blanks to get the properties you want. Or get creative and forge your own path!

##### Package

You can query a package for its properties:

```markdown
$.<PROPERTY>
```

For instance, to get the size:

```markdown
$.size
```

<details>

<summary>Properties</summary>

|       Property        |     Type     | Description                                        |
| :-------------------: | :----------: | -------------------------------------------------- |
|      `owner_id`       |    number    | The ID of the owner                                |
|     `owner_type`      |    string    | The type of owner (e.g. `users`)                   |
|    `package_type`     |    string    | The type of package (e.g. `container`)             |
|        `owner`        |    string    | The owner of the package                           |
|        `repo`         |    string    | The repository of the package                      |
|       `package`       |    string    | The package name                                   |
|        `date`         |    string    | The most recent date the package was refreshed     |
|        `size`         |    string    | Formatted size of the latest version               |
|      `versions`       |    string    | Formatted count of versions scraped                |
|       `tagged`        |    string    | Formatted count of tagged versions                 |
|      `downloads`      |    string    | Formatted count of all downloads                   |
|   `downloads_month`   |    string    | Formatted count of all downloads in the last month |
|   `downloads_week`    |    string    | Formatted count of all downloads in the last week  |
|    `downloads_day`    |    string    | Formatted count of all downloads in the last day   |
|      `raw_size`       |    number    | Size of the latest version, in bytes               |
|    `raw_versions`     |    number    | Count of versions                                  |
|     `raw_tagged`      |    number    | Count of tagged versions                           |
|    `raw_downloads`    |    number    | Count of all downloads                             |
| `raw_downloads_month` |    number    | Count of all downloads in the last month           |
| `raw_downloads_week`  |    number    | Count of all downloads in the last week            |
|  `raw_downloads_day`  |    number    | Count of all downloads in the last day             |
|       `version`       | object array | The versions of the package (see below)            |

</details>

##### Version

You can query a package version by replacing `<PROPERTY>` above with the following:

```markdown
version[<FILTER>].<PROPERTY>
```

For example, to get the `latest` tag(s), we can find the version with it and exclude it from the list:

```markdown
version[?(@.tags.indexOf("latest") != -1
)].tags[?(@ != "latest")]
```

Or to get the number of downloads in the last month for a version by name from a certain date:

```markdown
version[?(@.name=="<VERSION>"
       && @.date=="<YYYY-MM-DD>"
)].downloads_month
```

<details>

<summary>Properties</summary>

|       Property        |     Type     | Description                                    |
| :-------------------: | :----------: | ---------------------------------------------- |
|         `id`          |    number    | The ID of the version                          |
|        `name`         |    string    | The version name                               |
|        `date`         |    string    | The most recent date the version was refreshed |
|       `newest`        |   boolean    | Whether the version is the latest              |
|        `size`         |    string    | Formatted size of the version                  |
|      `downloads`      |    string    | Formatted count of downloads                   |
|   `downloads_month`   |    string    | Formatted count of downloads in the last month |
|   `downloads_week`    |    string    | Formatted count of downloads in the last week  |
|    `downloads_day`    |    string    | Formatted number of downloads in the last day  |
|      `raw_size`       |    number    | Size of the version, in bytes                  |
|    `raw_downloads`    |    number    | Count of downloads                             |
| `raw_downloads_month` |    number    | Count of downloads in the last month           |
| `raw_downloads_week`  |    number    | Count of downloads in the last week            |
|  `raw_downloads_day`  |    number    | Count of downloads in the last day             |
|        `tags`         | string array | The tags of the version                        |

</details>

### Database

The properties are generated from the following tables, which provide a historical record.

#### Packages

The general stats for all packages.

<details>

<summary>Schema</summary>

|      Column       |  Type   | Description                                     |
| :---------------: | :-----: | ----------------------------------------------- |
|    `owner_id`     | INTEGER | The ID of the owner                             |
|   `owner_type`    |  TEXT   | The type of owner (e.g. `users`)                |
|  `package_type`   |  TEXT   | The type of package (e.g. `container`)          |
|      `owner`      |  TEXT   | The owner of the package                        |
|      `repo`       |  TEXT   | The repository of the package                   |
|     `package`     |  TEXT   | The package name                                |
|      `size`       | INTEGER | The size of the latest version                  |
|    `downloads`    | INTEGER | The total number of downloads                   |
| `downloads_month` | INTEGER | The total number of downloads in the last month |
| `downloads_week`  | INTEGER | The total number of downloads in the last week  |
|  `downloads_day`  | INTEGER | The total number of downloads in the last day   |
|      `date`       |  TEXT   | The most recent date the package was refreshed  |

</details>

#### Versions

The stats for all versions of each package.

<details>

<summary>Schema</summary>

|      Column       |  Type   | Description                                     |
| :---------------: | :-----: | ----------------------------------------------- |
|       `id`        | INTEGER | The ID of the version                           |
|      `name`       |  TEXT   | The version name                                |
|      `size`       | INTEGER | The size of the version                         |
|    `downloads`    | INTEGER | The total number of downloads                   |
| `downloads_month` | INTEGER | The total number of downloads in the last month |
| `downloads_week`  | INTEGER | The total number of downloads in the last week  |
|  `downloads_day`  | INTEGER | The total number of downloads in the last day   |
|      `date`       |  TEXT   | The most recent date the version was refreshed  |
|      `tags`       |  TEXT   | The tags of the version (csv)                   |

</details>

### TODO

* [ ] Get sizes for all package types
