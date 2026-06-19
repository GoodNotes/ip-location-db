# GoodNotes IP Location DB Mirror

This repository mirrors the DB-IP city CSV gzip assets used by the GoodNotes
`ip-location` service.

The service reads these files from the repository root:

- `dbip-city-ipv4-num.csv.gz`
- `dbip-city-ipv6-num.csv.gz`

Keep both files at the root unless the corresponding service configuration is
updated in tandem:

```text
IPV4_GITHUB_FILE=dbip-city-ipv4-num.csv.gz
IPV6_GITHUB_FILE=dbip-city-ipv6-num.csv.gz
```

## Source

The data files are mirrored from the latest DB-IP city release published by
`sapics/ip-location-db`:

- https://github.com/sapics/ip-location-db/releases/download/latest/dbip-city-ipv4-num.csv.gz
- https://github.com/sapics/ip-location-db/releases/download/latest/dbip-city-ipv6-num.csv.gz

The sync workflow runs daily and can also be triggered manually from GitHub
Actions.

## License And Attribution

The DB-IP city Lite database is licensed under Creative Commons Attribution 4.0
International. The upstream license text is retained in `DBIP-LICENSE`.

Applications that display or use results from this database must attribute
DB-IP, including a link back to DB-IP.com for web applications:

```html
<a href="https://db-ip.com">IP Geolocation by DB-IP</a>
```

## Large File Caveat

The gzip assets are intentionally committed in-tree so unauthenticated GitHub
raw/API downloads work for the service. GitHub warns for files over 50 MiB and
blocks files over 100 MiB. If a dataset crosses 100 MiB, this mirror will need a
different storage or download strategy before the next update can be committed.
